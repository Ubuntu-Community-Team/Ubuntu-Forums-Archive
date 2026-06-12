---
title: "Wubi is being a jerk"
date: 2009-02-17
forum: General Help
---

### Post by Justin18 on 2009-02-17
Hello, 

I am posting this under "general help" because there seems to no longer be a "Wubi" help forum so feel free to move this topic to another part of te help forums. Anyways here's my problem. I have had Ubuntu 8.10 Intrepid Ibex installed on a compaq Presario for the past week and a half with no problems and am loving Ubuntu Linux untill today I was going to boot into Ubuntu after I ended using the windows side of the computer and turned off the computer when I started it up instead of asking me if I wanted to boot into Windows or Ubuntu it now has reverted back to booting directally into windows xp and not asking me. I am now on Ubuntu but I have to go through the "Boot options" while the computer is loading and boot from the hard drive and then it asks me which operating system I wish to boot into... Does anyone know how I can fix this problem and return it to where it asks me which OS I want to boot into by default?

Thanks

---

### Post by Tim Sharitt on 2009-02-17
Look in the windows boot.ini file (I believe it is in the root of the windows disk, may be hidden in windows) and see if the timeout has changed to zero or a small enough number to keep the menu from appearing.

Post the contents of the boot.ini if you can't make sense of it.

---

### Post by Justin18 on 2009-02-17
Here is the contents of the Boot.ini (backup) file. Sorry but a Backup was all I could find:

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

It appears that the timeout is not a small enough number but it still only boots into windows without asking

EDIT: I just found this one by going to "My computer and right clicking and choosing properties then going to the advanced Tab then choosing "Startup and recovery" and then choosing the "Edit" button and heres what I got 

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
c:\wubildr.mbr="Ubuntu"

---

