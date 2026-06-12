---
title: "problem use lirc on 9.04"
date: 2009-05-28
forum: General Help
---

### Post by nickt79 on 2009-05-28
Goodmorning everyone
i've just installed Ubuntu 9.04 on a Asus M2N68-VM.
I whant to use this pc like a HTPC with XBMC
I try many guides but no-one works with lirc :(

i've made an homebrew IR receiver and it works (don't work in ubuntu 9.04, but on windows yes)

i've installed lirc 0.8.5pre3
```
./configure --with-x --with-driver=serial
```and all works
when i try
```
irrecord --driver=serial --device=/dev/ttyS0 epson
```i receive
```
Driver `serial' not supported.
Supported drivers:
    default

```and nothing work.
then i try 
```

irrecord --device=/dev/ttyS0 epson

```and i have this output
```

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get hardware features
irrecord: this device driver does not support the LIRC ioctl interface
irrecord: major number of /dev/ttyS0 is 4
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyS0 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```i've already charged setserial, lirc_dev and lirc_serial

i've no idea why i've this problems :(

can someone have any ideas to help me?

thanks
bye
Nick

---

### Post by nickt79 on 2009-05-28
I've solved this problem
1) usingi lirc 0.8.4a
2) using (in this order) this steps (all are runned by root)
```

apt-get install libirman-dev
apt-get install setserial
setserial /dev/ttyS0 uart none
depmode -ae
modprobe lirc_serial
modprobe lirc_dev

```
on lirc source file
```

./configure --with-x --with-driver=serial
make && make install
chmod 777 /dev/lirc

```
now i craete the fiel with remote settings
```

irrecord namefile

```
set up lircd to use this file
1) only to try
```

lircd namefile
irw

```
2) insatll this settings on lircd.conf
```

killall lircd
mv nomefile /etc/lircd.conf
lircd
irw

```

now the problem i to use this settings on xbmc :)

bye
Nick

---

### Post by spxger on 2009-07-01
> **nickt79 said:**
> I've solved this problem
1) usingi lirc 0.8.4a
2) using (in this order) this steps (all are runned by root)
```

apt-get install libirman-dev
apt-get install setserial
setserial /dev/ttyS0 uart none
depmode -ae
modprobe lirc_serial
modprobe lirc_dev

```
on lirc source file
```

./configure --with-x --with-driver=serial
make && make install
chmod 777 /dev/lirc

```
now i craete the fiel with remote settings
```

irrecord namefile

```
set up lircd to use this file
1) only to try
```

lircd namefile
irw

```
2) insatll this settings on lircd.conf
```

killall lircd
mv nomefile /etc/lircd.conf
lircd
irw

```

now the problem i to use this settings on xbmc :)

bye
Nick

sorry for my English, I am Argentinian. I ask if you can put step by step what you did, because I have the same problem and I do not know how to fix it, I tried doing that, but I do not know if I'm doing things correctly ...

Thanks for the help ...

German.

---

