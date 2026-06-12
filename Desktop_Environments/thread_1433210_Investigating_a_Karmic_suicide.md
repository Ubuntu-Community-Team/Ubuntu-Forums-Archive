---
title: "Investigating a Karmic suicide"
date: 2010-03-18
forum: Desktop Environments
---

### Post by batosai on 2010-03-18
Hi,

Tonight, my Ubuntu Karmic (amd64) decided I couldn'd log in graphically or, to be precise, not to start X anymore : the GDM login page appears. I log in. No error is displayed. The screen goes blank for a second and I'm back to the gdm page. I can log in fine in a text console. So I tried to start X from there. No errors (EE) in the output or X log file, but X doesn't start either.

I tried to rename the xorg.conf file to disable my custom configuration (dual head with nVidia twinview) and let X autodetect everything, this time I get an error about X missing an nVidia driver.

So, I decided to get the logs to post here and cry for help. Here the fun begins : 
- I can't ssh to the machine (connection refused). I tried to restart the ssh server (/etc/init.d/ssh restart), the command outputs nothing.
- I can't ssh from the machine to the outside world : I get a Segmentation fault error. Fishy.

memtest86 returns no errors, Ubuntu boots fine from the CD-ROM.
There is a Windows (XP) partition on the drive, which runs fine. So a hardware problem is unlikely.

Is anyone interrested in investigating what could cause that kind of crash, before I reinstall from scratch ? I can afford a few days as I'm able to work on my laptop for the time being...

---

### Post by denarced on 2010-03-18
Do your grub titles blink?

---

### Post by batosai on 2010-03-19
No they don't. But there is a new problem. Today, grub only shows the rescue interface. No more menus, and when I try to boot up the system manualy, the kernel isn't even loaded.

Maybe it is a hardware problem after all : the hard drive is quite new (about 2-3 months). It's a SuperTalent 32GB SSD drive... I will do further tests and keep you posted.

---

### Post by batosai on 2010-03-20
Mmmm, I recreated my MBR and restored corrupted binaries by doing an install without formating the partitions. Everything works fine now.

I'm afraid the ssd drive might have write errors. But it can't be tested with conventionnal tools... Unless someone has a great idea, I'm afraid all I can do is increase my backup frequency and wait for the next failure :-/

---

### Post by asmoore82 on 2010-03-20
> **batosai said:**
> There is a Windows (XP) partition on the drive, which runs fine. So a hardware problem is unlikely.
That's extremely flawed logic.

For one thing, it's Windows.
Also, by definition the "partition" hides part of your hard drive from Windows, yes?

Boot a LiveCD and test the entire hard disk with this(non-destructive):
```
sudo badblocks -sv /dev/sda
```
^may need to use "/dev/hda" for older hardware.

---

### Post by batosai on 2010-03-20
[QUOTE=asmoore]That's extremely flawed logic.[/QUOTE]

I wasn't considering a hard drive failure at the time, flawed logic indeed.

[QUOTE=asmoore]Boot a LiveCD and test the entire hard disk with this(non-destructive):
```
sudo badblocks -sv /dev/sda
```
^may need to use "/dev/hda" for older hardware.[/QUOTE]

I'll do that with an additional -n switch (non destructive write) and post the results here.

---

