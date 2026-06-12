---
title: "lm_sensors"
date: 2005-11-12
forum: Desktop Environments
---

### Post by crag277 on 2005-11-12
I am trying to install lm_sensors on my machine in order to get the CPU fans to slow down from their maximum speed.  After much trouble I was fiunally able to get lm_sensors to attempt an install, but it gave the following error:

gcc -Wl,-rpath,/usr/local/lib -o prog/sensors/sensors prog/sensors/main.ro prog/sensors/chips.ro  -Llib -lsensors
lib/libsensors.so: undefined reference to `sensors_yylex'
lib/libsensors.so: undefined reference to `sensors_yyin'
lib/libsensors.so: undefined reference to `sensors_lex_error'
lib/libsensors.so: undefined reference to `sensors_yylineno'
collect2: ld returned 1 exit status
make: *** [prog/sensors/sensors] Error 1

I'm new to linux, so this means nothing to me.  Any help is appreciated.

-Eric

---

### Post by teaker1s on 2005-11-12
i believe you won't slow fan speed this utility only monitors to make sure system stays within set limits

---

### Post by crag277 on 2005-11-12
I was afraid of that, but I was getting conflicting information, so I thought it would be worth a try.  I did get it to install, but it said there was no driver for my hardware, the LPC47M15x chip.  This is strange because, because the lm_sensros website says that this is supported in version 2.9.0 and up, and I installed 2.9.1.  

Does anyone know of any software way to control fan speed on a computer that doesn't control it through the BIOS?

---

### Post by ToastedToad on 2005-11-12
First maybe try to install it by apt.

$ sudo apt-get install lm-sensors
$ sudo sensors-detect

Answer default to all questions until they ask you if you want to write to /etc/modules, then select yes.

At the end it will give you the modules that it found that you should need, insert them by:

$ sudo modprobe (xxxxx)
$ sudo sensors -s
$ sensors

---

