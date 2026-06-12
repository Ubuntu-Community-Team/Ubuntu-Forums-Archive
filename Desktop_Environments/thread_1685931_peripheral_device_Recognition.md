---
title: "peripheral device Recognition"
date: 2011-02-11
forum: Desktop Environments
---

### Post by shadowfax1 on 2011-02-11
In this case I have a video capture device but when plugged in (usb) the os doesn't recognise it.  Is there software (device manager) where you can a least identyfy it?
Thanxs

---

### Post by jerrrys on 2011-02-11
i don't know.  pull up a terminal and enter **lshw **and **lsusb**

---

### Post by shadowfax1 on 2011-02-11
Okay it recognizes the device in this case Diamond Multimedia VC500 VVC
Now what?


tency=0 maxlatency=20 mingnt=1 multicast=yes
             resources: irq:23 memory:fe02b000-fe02bfff ioport:c800(size=8)
marco@marco-System-Product-Name:~$ lsusb
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 07de:2820 Diamond Multimedia VC500 Video Capture Dongle
Bus 001 Device 003: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
marco@marco-System-Product-Name:~$

---

### Post by jerrrys on 2011-02-11
have you simply tried a restart with the device plugged in ?

---

### Post by shadowfax1 on 2011-02-11
Yes but still nothing...It's recognized in device manager but right clicking it doesn't give you any options...could it be a sudo make device?

---

### Post by jerrrys on 2011-02-12
all i find on this is basically other people asking the same question with no reply...

maybe you should go to the manufacture and ask if linux support is available.  another thought would maybe be force mount, something i have not tried.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=force+mount+usb&as_qdr=all&sa=Google+Search&lang=en#847](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=force+mount+usb&as_qdr=all&sa=Google+Search&lang=en#847)

---

