---
title: "Hibernation &amp; Suspend to RAM"
date: 2005-12-20
forum: Desktop Environments
---

### Post by ashrack on 2005-12-20
They both work great 4 me if I have VESA as the driver in "xorg.conf"
But if I change the driver to "NVIDIA" they both fail.

I've installed NVIDIA drivers using this guide:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

I would really like to get SUSPEND 2 RAM working, HIBERNATION would be good also but it's not a priority as long as SUSPEND 2 RAM's working

Here's the "xorg.conf" file:
[http://www2.arnes.si/~aurank1/xorg.conf]("http://www2.arnes.si/~aurank1/xorg.conf")

---

### Post by markr on 2005-12-20
Try this to get suspend working (it did for me on my dell inspiron 5150) :

[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29%7C%28nvidia%29](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29%7C%28nvidia%29)

I'm still working on hibernation though...

Mark.

---

### Post by ashrack on 2005-12-20
The machine now boots from suspend or hibernation but I have the following problems then:
1. When I delete a file it will take almost a minute, even if it's size is 20KB
2. Text mode is garbled up (CTRL+Alt+F1)
3. Gnome System monitor won't even start.
4. Some other minor problems.

Anyway to fix them?

---

### Post by ashrack on 2005-12-21
*bump* Would really like to get S3 or hibernation working.
btw. Why doesn't NVIDIA fix them drivers if they cause S3/hibernation to breake?

---

### Post by ashrack on 2005-12-22
*bump2*

---

### Post by ashrack on 2005-12-24
So apperantly theres no sollution.
:(

---

### Post by henok on 2006-02-04
I followed the instructions @

[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29%7C%28nvidia%29](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29%7C%28nvidia%29)

but my system's powers are still running and only the screen goes out.

Then it does not return from suspend (I tried the power button).

---

### Post by ashrack on 2006-02-04
HENOK
I've already fix that. By using SUSPEND2  and some optimizations in hibernate.conf

---

### Post by henok on 2006-02-04
[QUOTE=ashrack]HENOK
I've already fix that. By using SUSPEND2  and some optimizations in hibernate.conf[/QUOTE]

asharck,

how did you implement SUSPEND2?
which kernel do you have and which one is necessary for SUSPEND2?
what does your /etc/X11/xconf.conf "Device" section look like (do you have nvidia)
what does your /etc/default/acpi-support look like (what did you change?)
where is hibernate.conf located? and why use that for suspend? (should it not be suspend.conf?)

I would really appreciate your help.

---

### Post by ashrack on 2006-02-04
[QUOTE=henok]asharck,

how did you implement SUSPEND2?
which kernel do you have and which one is necessary for SUSPEND2?
what does your /etc/X11/xconf.conf "Device" section look like (do you have nvidia)
what does your /etc/default/acpi-support look like (what did you change?)
where is hibernate.conf located? and why use that for suspend? (should it not be suspend.conf?)

I would really appreciate your help.[/QUOTE]
I implemet SWSUPE2 by a help of this guide:
[http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)
I believe U should be able to find all your answers in there. 
Am sorry for not beig specific enough I've currently susscceded only in hibernation for 2 of my machines. One running the default RADEON driver and on running the NVIDIA propriety driver. My next step is to enable SUSPEND TO RAM pr S3. But I haven't have the time yet

---

