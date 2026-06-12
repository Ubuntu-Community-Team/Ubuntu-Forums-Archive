---
title: "Repair of Ubuntu"
date: 2009-06-16
forum: General Help
---

### Post by wide-load on 2009-06-16
I'm running version 9.04 on a AMD Dual 6400+.  My system is dual boot, to Windows XP, with a separate SATA drive for each OS.  The other day there was a power fail at my house with Ubuntu running.  When I attempted to reboot Ubuntu it doesn't work right.  On the first boot it ran fsck and found several errors, which it repaired.  When I boot I get many errors.  Each error starts out with a number.  These start out as a 2 digit number followed by a 6 digit number in the form xx.xxxxxx.  The predominate message is ata3.00 Status {DRDY ERR}, then ATA3.00 error {UNC}. Next would be Exception Emask followed by numbers. Then next is IRQ Stat.  The next message is CMD 25/00 followed by some numbers.  The next message is RES 51/40 followed by the same numbers in the message above.  The messages fly by so fast I can't read them and write them down.  The number in front of the error messages increments, getting up in the range of several hundred.

This process continues on for a few minutes and finally Ubuntu starts.  It doesn't work right however.  The printer doesn't work, Sound doesn't work and Update Manager doesn't work.  Most of the applications on the APPLICATIONS menu,that I've tried, work.

When I shut down the system I get the same kinds of error messages.  It takes a while to shut down before the system powers off.

What I'd like to know is there a program that will surface scan my hard drive similar to SCANDISK of Windows?

Is there a way I can repair a contaminated copy of Ubuntu, if my hard drive hasn't incurred damage.  I'd like to repair, if that is possible, rather than reload from CD which means I'd have to update several hundred updates to get it up to current. If my hard drive has incurred damage I'll have to reinstall a new copy of Ubuntu on a new drive.  I have backed up my documents, pictures, etc., in case I have to reinstall a fresh copy.   

I'm relatively new to Ubuntu so I need some guidance here.

---

### Post by wide-load on 2009-06-19
Well, I'm a little surprised.  I have used Forums several times  in the past and had good response.  However this time I haven't heard any suggestions from anybody.

The situation has since degraded.  I made a mistake and ran sudo fsck, from terminal.  It seemed to find a lot of errors and fix them.  What really happened is that I've now made Unbuntu inoperable.  So now it looks like, because of my own foolish mistake, I have no choice but to reinstall a fresh copy of Unbuntu.  I would still like to know if there is anything I can run from the command line interface, or live CD that will surface scan my hard drive.

---

### Post by merlinus on 2009-06-19
Try testdisk or systemrescuecd.

---

### Post by 73ckn797 on 2009-06-19
You may want to boot from the LiveCD and from synaptic install "smartmontools". That will scan the drive for you.

If you can get into the system without booting from disk and can install it there, try it.

Here is a link to the program but it is in synaptic: [http://sourceforge.net/projects/smartmontools/](http://sourceforge.net/projects/smartmontools/)

---

### Post by wide-load on 2009-06-23
> **73ckn797 said:**
> You may want to boot from the LiveCD and from synaptic install "smartmontools". That will scan the drive for you.

If you can get into the system without booting from disk and can install it there, try it.

Here is a link to the program but it is in synaptic: [http://sourceforge.net/projects/smartmontools/](http://sourceforge.net/projects/smartmontools/)

I went to another system and installed smartmontools on it, using synaptic.   I wanted to learn how to use it on a working system before I used it on the system that is in trouble.  But I can't seem to find out how to start the application.  I assumed it would appear under SYSTEM, Administration or APPLICATIONS, but it doesn't.  Any advice would be helpful,

---

### Post by mgranet on 2009-06-23
It's a command line only tool.
```
sudo smartctl -*options* /dev/*xxx*
```

---

### Post by 73ckn797 on 2009-06-23
> **wide-load said:**
> I went to another system and installed smartmontools on it, using synaptic.   I wanted to learn how to use it on a working system before I used it on the system that is in trouble.  But I can't seem to find out how to start the application.  I assumed it would appear under SYSTEM, Administration or APPLICATIONS, but it doesn't.  Any advice would be helpful,


Look in Synaptic for "gsmartcontrol". It is the graphical front end for "smartmontools". It will then be found in Applications/System Tools after installation.

---

