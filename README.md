# minimosd-extra

refactored a bit - now uses much less memory and can use less EEPROM

also MAX7456 renew doing in VSYNC to get rid of "snow" on screen - like 
in http://forum.rcdesign.ru/f90/thread132831-195.html#post5602416 but on interrupt instead of polling via SPI.

Also PSTR to all strings

NEW FEATURES:

4 screens instead of 2

individual control of sign icon of each panel per screen

voltage, current & RSSI can be used from external pins

TLOG player in configurator - now settings can be checked without working plane/copter!

RADAR (like in MiniNAZAosd) and ILS in Horizon, can be enabled individually

horizon angles can be adjusted, indepentently in PAL and NTSC

PAL/NTSC detected dynamically - now can use different cameras!

screen offsets via configurator

can use additional pins (that can be found on some boards) for measuring 2nd battery current and voltage

new GPS coords - in one line

Any RC channel can be translated to output pin (eg. for cameras switch)


ATTENTION! this version is NOT compatible with original MinimOSD tools!

/* RUSSIAN */

Отрефакторил, убрав чудовищный расход памяти на хранение всех настроек всех возможных экранов сразу, также 
убрал "регистры" флагов (и все с ними связанное) в пользу хранения вместе с координатами. Ну и по 
мелочи - PSTR, PROGMEM и отказ от ненужных статических массивов. 

В результате имеем свободных 721 байт вместо 160 в оригинале. 

Также сделано обновление памяти MAX7456 во время VSYNC дабы избавиться от "снега" на экране из-за помех, по мотивам
http://forum.rcdesign.ru/f90/thread132831-195.html#post5602416 но через прерывание вместо странного поллинга 
через SPI.

Также сделана регулировка отступов от края экрана, пока через define но в планах также через конфигуратор

НОВЫЕ ВОЗМОЖНОСТИ!

Объединены самолет и коптер, выбор производится по значению из EEPROM и может МЕНЯТЬСЯ НА ЛЕТУ!

Уменьшен расход EEPROM в три раза (!). В результате можно задать 4 экрана вместо 2-х и при этом куча свободного места под новые параметры.

Чтение-запись EEPROM в цикле а не индивидуальными байтами - нет больше длинных "портянок"

Видимость иконок - обозначений каждой "панели" задается индивидуально, независимо по экранам

Напряжения, токи и RSSI могут читаться с дополнительных выводов (со сглаживанием по 8 отсчетам),
источник и поправочные коэффициенты задаются в конфигураторе независимо

Переключение экранов может производиться по внешнему PWM для использования с номерами каналов выше 8

В авиагоризонте сделаны поправочные коэффициенты (независимые для PAL и NTSC), и добавлен "Радар" (по мотивам МиниНазаОСД). 

Видимость Радара и ILS задается индивидуально.

Изменена логика формирования "панелей", так что теперь мелкие панели могут использовать незадействованные области крупных панелей. 
Это позволило отрисовывать радар, ILS и центральный маркер в пределах авиагоризонта

Переключение PAL/NTSC производится "на лету", без перезагрузки - позволяя использовать две камеры разных форматов

в коде сделан отладочный HEX-дамп прямо на экран

В конфигураторе сделан плеер TLOG - теперь можно проверить работу OSD без самолета/коптера.

Смещение экрана относительно синхроимпульсов задается через конфигуратор

Изменен шрифт для отображения всех новых вкусностей

Сделан вариант отображения координат GPS в одну строку

Добавлена возможность вывода любого канала наружу в PWM 

После всего этого остается свободно 525 байт памяти и 2+к флеша.


Внимание! Эта версия несовместима с утилитами из оригинальной MinimOSD!