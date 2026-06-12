---
title: "Samsung Galaxy Ace on Ubuntu"
date: 2011-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by techbongo on 2011-10-17
I'm using Samsung Galaxy Ace S5830. My phone needs a software to configure the phone drivers. The software is called Kies.
But this software is Windows compatible. When I connect my phone using USB in Ubuntu, it doesn't detect the phone (not even as a storage device).

Can you please tell how to connect my phone in Ubuntu for File Transfer etc? Is there a Kies alternative for Ubuntu?

Note: My mobile uses Android OS.

Many Thanks.

---

### Post by sasanb on 2011-12-17
Hi, I have the same problem. I try turning off "USB Debugging" as suggested elsewhere and still nothing.

typing lsusb I get 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 047d:1030 Kensington 
Bus 001 Device 044: ID 04e8:681d Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone

So the phone is there and detected by operating system, except that there is no way to mount it. I am using Ubuntu 11.10 and my phone is on Android 2.3.5.

---

### Post by ugm6hr on 2011-12-18
I presume it mounts the SD card OK?
I think this is something to do with the way that Android mounts the phone's internal memory - it's not possible for it to be mounted on both the phone and on your computer at the same time.

---

### Post by migrate from windows on 2011-12-21
I have the same mobile android 2.3.4

It works a s a storage device out of the box! I run ubuntu 10.10.

I plug the cable
pull down the notifications tab in the phone
tap on select to copy files from /to.....
tap on connect  storage to pc
click ok in the next dialog box
that's it there's a drive icon on the ubuntu desktop!!!!!!

(usb debugging checked)

---

### Post by sasanb on 2011-12-22
Thanks "Migrate From Windows" for the helpful comment, it actually worked. :D

---

### Post by paulbuk on 2012-01-04
> **migrate from windows said:**
> I have the same mobile android 2.3.4

It works a s a storage device out of the box! I run ubuntu 10.10.

I plug the cable
pull down the notifications tab in the phone
tap on select to copy files from /to.....
tap on connect  storage to pc
click ok in the next dialog box
that's it there's a drive icon on the ubuntu desktop!!!!!!

(usb debugging checked)

Ditto. Follow the above for simple transfer via USB.
I just bought a Samsung Galaxy Y, to test the Android phone, the above works great and TOPS with Ubuntu 10.10 prior to an 11.04 upgrade on my desktop.
((-:

PB

All my M$ comps have been consigned to the skip. Period!

---

### Post by 1clue on 2012-01-04
I thought Kies was the same as Kies Air, but evidently not.

I have a Samsung Galaxy S2, which has Kies Air.  I run that and it says go to [http://192.168.232.216:8080/](http://192.168.232.216:8080/) from the computer.  I do that, and the phone is a web server with access to pictures, video, music, whatever.

---

### Post by jean noel on 2012-02-24
Just bought a Galaxy Ace to replace my aging SGH E-250. The above solution worked perfectly for me too. Absolutely top notch advice.
Regards

---

### Post by eddier on 2012-06-17
Sorry to pull this one from the graveyard but a usable app called Airdroid has sorted things for me.

Install it on your phone,when selected you can connect with your browser.

I got fed up trying to find my blutooth adapter!

eddie

---

