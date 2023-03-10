# ТЕМА №6: Хэширование, шифрование, кодирование

## Кодирование

Кодирование – процесс преобразования доступной нам информации в информацию понятную для нужных систем, удобного хранения и автоматической переработки.
- Цифровое устройство по умолчанию не понимает символы — только числа. Поэтому буквы, цифры и знаки приходится кодировать, чтобы задавать компьютеру соответствие между определенным начертанием и числовым значением. Сейчас вариантов кодирования несколько, и ASCII — одна из наиболее ранних кодировок. Она задала стандарты для последующих решений.

[ASCII (АСКИ)](https://ru.wikipedia.org/wiki/ASCII) — это таблица кодировки символов, в которой каждой букве, числу или знаку соответствует определенное число. В стандартной таблице ASCII 128 символов, пронумерованных от 0 до 127. В них входят латинские буквы, цифры, знаки препинания и управляющие символы.
Таблицу разработали в Америке в 60-х, и ее название расшифровывается как American Standard Code for Information Interchange — Американская стандартная кодировка для обмена информацией. Аббревиатура читается как «аски».

---
## Шифрование

Шифрование – это процесс изменения информации в иную форму таким образом, чтобы её смогли прочитать только нужные пользователи. При этом эти пользователи знают **ключ** и/или алгоритм изменения полученных данных к исходному значению. 

#### Виды:
1) Симметричное шифрование:
Использует один криптографический ключ для шифрования и дешифрования данных.
Использование одного ключа для обеих операций делает процесс простым и очень быстрым. Такой подход например активно используется для шифрования больших объемов данных. Посторонним лицам может быть известен алгоритм шифрования, но неизвестна небольшая порция секретной информации — ключа, одинакового для отправителя и получателя сообщения; Примеры: DES, 3DES, AES, Blowfish, Twofish, ГОСТ 28147-89

2) Асимметричное шифрование
В отличие от симметричного, включает в себя несколько ключей для шифрования и дешифрования данных, которые математически связаны друг с другом. Один из этих ключей известен как «открытый ключ», а другой — как «закрытый ключ». 
Если есть необходимость безопасно общаться с сотнями собеседников непрактично и неудобно использовать разные ключи для каждого собеседника.
Чтобы решить эту проблему, используется шифрование с открытым ключом. Создается открытый ключ и передается каждому, кто отправляет информацию, а секретный (закрытый) ключ хранится при себе. Собеседникам поручается зашифровать информацию с помощью открытого ключа, чтобы данные можно было расшифровать только с помощью личного "закрытого" ключа. Это исключает риск компрометации, поскольку данные могут быть расшифрованы только с использованием закрытого ключа, который есть у создателя.

Короче говоря, метод асимметричного шифрования гарантирует, что данные при передаче не были подменены человеком посередине, но процесс шифрования и дешифрования данных в сравнении с симметричным подходом является ощутимо мучительно медленным. 

| Симметричное шифрование |Асимметричное шифрование|
|------------------------|------------------------|
| Один ключ используется для шифрования и дешифрования данных. | Пара ключей используется для шифрования и дешифрования. Эти ключи известны как “открытый ключ” и “закрытый ключ”. |
| Более простой метод шифрования, так как используется только один ключ. | В связи с тем, что используется пара ключей — процесс более сложный. |
| Используется для шифрования большого объема данных. | Обеспечивает аутентификацию. |
| Обеспечивает более высокую производительность и требует меньше вычислительной мощности. | Сложные процессы протекают медленнее и требуют большей вычислительной мощности. |
| Для шифрования данных используется меньшая длина ключа (128-256 бит).	| Используются более длинные ключи шифрования (1024-4096 бит). |
| Идеально подходит для шифрования большого количества данных.| Используется при шифровании небольшого объема данных. |
| Стандартные алгоритмы: RC4, AES, DES, 3DES и QUAD. | Стандартные алгоритмы: RSA, Diffie-Hellman, ECC, El Gamal и DSA. |

### Основная суть шифрования:
- конфиденциальность – данные скрыты от посторонних
- целостность – предотвращение изменения информации
- идентифицируемость – возможность определить отправителя данных и невозможность их отправки без отправителя

История развития шифрования идет еще со времен возникновения человеческой цивилизации и применялось еще задолго до создания компьютеров и информатики как таковой. Но что там было раньше нас программистов мало интересует.

Основных алгоримов шифрования много, но самым надежным считается алгоритм RSA
- На сегодняшний день является наиболее используемым алгоритмом асимметричного шифрования. По сути, выбираются два различных случайных простых числа заданного размера (например, 1024 бита каждое) и умножаются, чтобы создать еще одно гигантское число. Задача состоит в том, чтобы определить исходные простые числа из умноженного гигантского. Оказывается, эта головоломка практически невозможна для современных суперкомпьютеров, не говоря уже о людях.
- В 2010 году группа добровольцев провела исследование, и им потребовалось более 1500 лет вычислительного времени (распределенного по сотням компьютеров), чтобы взломать 768-битный ключ RSA, что намного ниже стандартного 2048-битного, который используется сегодня.

---

## Хеширование:

Под хешированием представляют процесс работы хеш-функции. Результатом ее работы является хеш. 
- Если кратко, хеширование - это односторонний математический алгоритм, преобразовывающий произвольный набор данных в состоящую из букв и цифр строку фиксированной длины. Причем длина эта будет оставаться неизменной, вне зависимости от объема вводных данных. Под "односторонним" подразумевается возможность перевести данные в хеш, но хеш в исходные данные перевести практически невозможно.

#### Зачем?

1. Хранение секретов, чаще всего пароли или иные личные данные. Разные алгоримы хэширования паролей могут использовать различные модификаторы, например [Соли](https://ru.wikipedia.org/wiki/%D0%A1%D0%BE%D0%BB%D1%8C_(%D0%BA%D1%80%D0%B8%D0%BF%D1%82%D0%BE%D0%B3%D1%80%D0%B0%D1%84%D0%B8%D1%8F)).
    -- онлайн-сервис в идеале не хранит пользовательские пароли в виде обычного текста. Вместо этого он хранит их в виде хеш-значений. То есть сервис не хранит ваш пароль в исходном виде, а только его хеш.
2. Использование в хеш-таблицах.
    -- Хеш используется в качестве ключа в хеш-таблицах.
3. Защита медиафайлов.
    -- Например Dropbox. Владелец защищенного копирайтом контента имеет на руках хеш-коды определенных аудио- и видеофайлов, запрещенных к распространению, и занесит их в список блокируемых хешей. Когда пользователь предпринимает попытку незаконно распространить некий контент, автоматические сканеры Dropbox засекают файлы, чьи хеши оказываются в пресловутом списке, и блокируют возможность их распространения.
4. Защитное ПО, антивирусы.
    -- хеширование широко используется для детектирования зловредных программ

#### Пример
Возьмем один из популярных, алгоритмов шифрования SHA-1

| Information | SHA1 |              Hash                        |
|-------------|-----|------------------------------------------|
| b           | ->  | e9d71f5ee7c92d6dc9e92ffdad17b8bd49418f98 |
| Brian       | ->  | 75c450c3f963befb912ee79f0b63e563652780f0 |
| Brain       | ->  | 97fb724268c2de1e6432d3816239463a6aaf8450 |
| brian       | ->  | 760e7dab2836853c63805033e514668301fa9c47 |
| The red fox jumps over the blue dog | -> | 0fec050f02cd6201e2ef871ecf8f9d94c1dab7ae | 

Как мы можем увидеть, между ними нет ничего общего, и при любых исходных данных мы получаем хеш одинаковой длины.

---

## Заключение
Таким образом, все три термина – шифрование, кодирование и хэширование – используются для преобразования данных из одной формы в другую для безопасности передачи или удобства распознавания. 
Однако, кодирование применяется не для защиты данных, а всего лишь для приведения массивов данных в удобочитаемый для системы формат и размер. А Шифрование и хэширование, наоборот, отвечают за сохранность информации при передаче и хранении.
