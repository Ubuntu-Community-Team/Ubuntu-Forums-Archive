---
title: "16 sec. boot time (crazy)"
date: 2006-07-08
forum: Desktop Environments
---

### Post by nimes on 2006-07-08
hi, 
Pardus 1.1 alpha, Turkish operating system based on linux, boot up at 16 sec.

[http://cekirdek.pardus.org.tr/~caglar/blog/blog.cgi?file=mudur.blog](http://cekirdek.pardus.org.tr/~caglar/blog/blog.cgi?file=mudur.blog)

Ubuntu Edgy Eft boot time ??

---

### Post by viraptor on 2006-07-08
If it supports init-ng? Something similar to that time, probably...
But init-ng isn't really ready yet AFAIR... right?

---

### Post by FredB on 2006-07-08
And 16 seconds ? Do you really need such a quick boot ? My P4 2.6 ghz - 1 Gb boots in 40 to 50 seconds. I don't need to see it boot faster ;)

---

### Post by patrickfromspain on 2006-07-08
50 secs from to gnome fully loaded? With the stoc kernel? I get 1 min with a custom one... on an Athlon64 3200+ with 1gig of ram..

---

### Post by Anduu on 2006-07-08
Frankly I can't understand why so many people are looking to reduce their boot times....Linux is not Windows...you don't have to reboot 10 times a day to maintain a stable system.

With all the stuff I have got loading at startup I'm looking at near 2 minutes to boot and I don't care ;)

---

### Post by Zmija on 2006-07-08
i-Ram or Maxtor Atlas 15K II ??? ;)

EDIT: my boot is about 60 sec.. from push of a power button to desktop... (see sig. ;) )

---

### Post by viraptor on 2006-07-09
I'd say - when you're on a battery - 2 minutes of full cpu / io load is something. It's more of something, if cpu gets hot and decides to switch acpi mode and insert some nops to cool down and run even slower (after reboot typically)... Especially it's something - if you can compress that to parallel init and do it in 30 secs.

I mostly leave my laptop on ram hibernation - 2 secs to login screen with all apps preloaded. It's REALLY convenient - try that for some time and then try to come back to normal boot every time. It's almost impossible... ;)

---

### Post by halfvolle melk on 2006-07-09
> A unique feature of LinuxBIOS is that the x86 version runs in 32-bit mode after executing only sixteen instructions. (Almost all other x86 BIOS'es run exclusively in 16-bit mode.) Running in 32-bit mode makes it run very fast (its current cold boot record is 3 seconds).
But I don't think it's running X ;)
[http://www.linuxbios.org/index.php/Main_Page](http://www.linuxbios.org/index.php/Main_Page)
[http://en.wikipedia.org/wiki/LinuxBIOS](http://en.wikipedia.org/wiki/LinuxBIOS)

---

