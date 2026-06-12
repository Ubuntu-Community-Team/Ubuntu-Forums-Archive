---
title: "Dual boot problem"
date: 2010-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kismeras on 2010-05-20
Hey Everyone, 
I have a Dell Vostro 3500...here are the specs:

Dell Vostro 3500 Laptop
Intel Core i5-520M (2.40GHz)
6GB,DDR3,1066MHZ
Dell Keyboard 86 Backlit English Vostro
Nvidia Geforce 310M, 512MB Graphics
500GB 7200RPM SATA Hard Drive
Palmrest with Fingerprint reader Winery 15
Dell,Software,Digital Persona Inc,Fingerprint Reader
Dell Wireless 365 Bluetooth 2.1 Module
8X DVD+/-RW with double-layer DVD+/-R write capability
Dell Wireless 1520 802.11n Half-Mini Card

I recently installed Ubuntu 10.04 alongside Windows 7 Pro X64. The install went well and i can boot into Ubuntu just fine. 
Here is the problem i am having:
When i reboot and choose Windows 7 i can no longer use my fingerprint reader. I get a msg saying reader not found. I uninstalled Ubuntu and the reader started working again. 
My Question is why would a dual boot mess up the reader on the windows side and how can i fix that?

Thanks.

---

### Post by kismeras on 2010-05-22
Anyone have any ideas?

---

### Post by binary10 on 2010-05-22
Did you originally have it protecting the boot up with a finger swipe ? 
 My old samsung X25 which had finger print protection which I seem to remember would write the image data to a small part of the disk at the start area of the disk maybe that's been removed by grub or something.

---

### Post by kismeras on 2010-05-22
I'm not sure if the software itself set something like that up. I just installed it and used it to log into windows. How would i check that?

---

### Post by binary10 on 2010-05-22
Not really knowing much about the dell finger print, I can't help much with the specific other than apply my own experience with other hardware implementations.

I just suspect that the image data was maybe at the start of the disk which has now been overwritten.

Sorry - not much help I know... My old (broken and sadly missed) samsung X25 use to have a registration and initialization utility to re-do the finger print setup. Maybe they you have to re-do that sequence in Win7.

---

### Post by kismeras on 2010-05-22
After i uninstalled Ubuntu it started workign fine. I'll reinstall Ubuntu then see if reinstalling the fingerprint software fixes the issue in Windows 7......good idea.

---

### Post by kismeras on 2010-05-28
I installed Linux Mint 9 and no issues with the fingerprint reader when i go back in to Windows.....haven't really been in Windows much though :)

---

