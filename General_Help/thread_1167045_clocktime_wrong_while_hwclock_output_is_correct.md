---
title: "clock/time wrong while hwclock output is correct"
date: 2009-05-22
forum: General Help
---

### Post by deepclutch on 2009-05-22
Hello ,
I am on 9.04 jaunty Ubuntu(Gnome).I am facing this issue of wrong time everytime I reboot the machine.
No UTC for India.but the current time shown in Gnome-Panel clock-applet is : 4:12PM May 22.This is wrong.
While ,hwclock output shows the correct time!.Why is it So?:o
```
root@sher:~# hwclock --show
Fri 22 May 2009 09:43:20 PM IST  -0.990445 seconds
```Even if I do a " hwclock --hctosys " ,next reboot and the time shown in Gnome Panel may be wrong.
Any Fix?
BTW ,here is the content of /etc/default/rcS for My System:
```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
RAMRUN=yes
RAMLOCK=yes
```

---

### Post by Shukuyir on 2009-05-22
I might have had the same problem once. I had set gmt_time in the preferences of the clock in the configuration editor set to true.

---

### Post by deepclutch on 2009-05-22
@Shukuyir:that's the same ,it enables UTC time.you can do it via /etc/default/rcS file.

---

### Post by Shukuyir on 2009-05-22
The file /etc/default/rcS on mine has "UTC" set to "yes" but have got the setting "gmt_time" of the clock preferences set to false

---

### Post by deepclutch on 2009-05-22
while I don't want UTC =YES . :(

---

### Post by deepclutch on 2009-05-22
atlast solved.the problem happened because I pulled util-linux-2.15 from debian :P ,which included /etc/init.d/hwclockfirst.sh -I removed that script .now using util-linux,udev,libblkid,initramfs-tools from ubuntu karmic repo.this solved.

---

### Post by revoltism on 2009-10-25
How did you change? I have the same problem but do not have an /etc/init.d/hwclockfirst.sh -I what i could se. When i sudo hwclock -r it tell me i got "util-linux-ng 2.16". 

How did you change to util-linux?

---

### Post by mgmiller on 2009-10-25
I had all kinds of crazy time problems in one of my computers.  Turned out the time was set wrong in BIOS.  Make sure it's correct there.  Many BIOS use 24 hour time, so make sure it's set correctly, 14:00 if you want 2:00 PM for example.  

Also, make sure your mobo battery is good.  One of the signs of a failing battery is clock weirdness.

---

### Post by revoltism on 2009-10-25
> **mgmiller said:**
> I had all kinds of crazy time problems in one of my computers.  Turned out the time was set wrong in BIOS.  Make sure it's correct there.  Many BIOS use 24 hour time, so make sure it's set correctly, 14:00 if you want 2:00 PM for example.  

Also, make sure your mobo battery is good.  One of the signs of a failing battery is clock weirdness.

Thanks for the quick reply. As the hwclock is correct and a hwclock -s corrects the time.. but then it drift off again. I do not think the fault is the battery. My bios clock is correct.

---

