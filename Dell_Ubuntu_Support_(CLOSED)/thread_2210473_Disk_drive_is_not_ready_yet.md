---
title: "Disk drive is not ready yet?"
date: 2014-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leny665 on 2014-03-11
I installed Lubuntu on a Dell Latitude CPx (Pentium III) using the alternate installer. The installation seemed to install correctly but after completion reboot the Lubuntu screen appears and it looks like its loading and then I get a message, "The disk drive for /dev/mapper/crypt swap 1 is not ready yet", and it gives 3 options, continue to wait, or press S to skip , or M for manual recovery. I have tried all 3 but it doesn't seem to do anything. It goes to a dark screen and does nothing.

---

### Post by Bucky Ball on 2014-03-11
Welcome. What release are you using (12.04 LTS, 13.10, etc.)? Sounds like it may be having issues with the /swap partition. You set one up during the partitioning section?

Also, will check the system requirements, but unsure what result you'll get using a PIII. How much RAM do you have? You are using the alternate because the desktop version wouldn't work?

---

### Post by leny665 on 2014-03-11
The release is 13.10 Alt. Yes, I used the alternate because the desktop would not work. It looks to have 256 MB RAM and a 2GB Hard drive.

---

### Post by ibjsb4 on 2014-03-11
Google tells me it has a 12G HDD.

/dev/mapper/crypt swap 1 is not ready yet

A possibility

[http://askubuntu.com/questions/56843/could-not-mount-dev-mapper-cryptswap1](http://askubuntu.com/questions/56843/could-not-mount-dev-mapper-cryptswap1)

---

### Post by Bashing-om on 2014-03-11
@ ibjsb4,

We need to know if any part of the file system was intentionally encrypted. If only swap is encrypted. That we can revert back to a normal swap partition and no harm done.
If any other portion of the file system is encrypted, it is beyond my knowledge or abilities.

[INDENT][INDENT]another case of 
[INDENT][INDENT][INDENT]depends
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by leny665 on 2014-03-13
During the install process, I was asked if I wanted encrypted and I declined.

---

### Post by Bashing-om on 2014-03-13
leny665; Well then.

Let's go to work on this:

First we have to make sure that swap is indeed encrypted:
Post back the output of all these terminal commands:
```

sudo blkid | grep swap

```

check for encrypted partitions:
```

sudo dmsetup status
ls /dev/mapper
ls -la /etc/uswsusp.conf
cat /etc/fstab

```

And in preparation to revert the swap partition, what partition are we looking at ?
```

sudo blkid
sudo fdisk -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Looks like a lot to know about but ->
[INDENT]the 7 P's apply
[INDENT][INDENT]Prior Prudent Planning Prevents P*** Poor Performance
[/INDENT][/INDENT][/INDENT]

---

### Post by leny665 on 2014-03-13
I can't get a terminal command; tried Ctrl-Alt-t.

---

### Post by Bashing-om on 2014-03-13
leny665; Humm ??

Are we looking at deeper problems ? From the desk top key combo ctl+alt+t gets a terminal also in Lubuntu. 

How about a console ? At the GUI log in what results from key combo ctl+alt+F1 ? Can you there log into the system (username and then password - no response to the screen when pass word is entered)?


We got to have a means to communicate with the operating system !

---

