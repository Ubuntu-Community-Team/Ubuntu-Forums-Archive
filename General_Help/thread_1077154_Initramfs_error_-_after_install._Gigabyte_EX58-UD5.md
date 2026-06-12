---
title: "Initramfs error - after install. Gigabyte EX58-UD5"
date: 2009-02-22
forum: General Help
---

### Post by rudihawk on 2009-02-22
Hey all!

After installing Hardy Heron on my new PC, I am unable to boot into the OS. After grub and the orange bar bouncing backwards and forwards a couple of times, I get dropped to a busybox shell with the following displaying on the screen:
```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay =(did the system wait long enough)
-Check root = (did the system wait for the right device?)
-missing modules (cat /proc/modules ;ls /dev)

Alert /dev/disk/by-uuid/sf93855b-d3et-494e-aaba-112e764fss9 does not exist. Dropping to a shell.


```

My specs:
Intel Core i7 920
Gigabye EX58-UD5
6GB of RAM
Nvidia GTX280 1024Mb
2 X 500GB Seagate Barracudas

I have tried booting it with the following command:

all_generic_ide floppy=off irqpoll

Help anyone?

---

### Post by rudihawk on 2009-02-25
Bump, anyone?

---

### Post by rbrauns on 2009-03-07
I just updated to the new kernel 2.6.28-11 ultimate and get the same error.  I have an Abit IC7, P4.  Booting using the old kernel works fine.  How did you fix the problem?

---

### Post by rudihawk on 2009-03-07
I didn't fix it, I have no idea what to do, basically waiting for 9.04 to come out and goin to try and install that, unless someone else can offer up another solution?

---

### Post by Tteddo on 2009-03-08
> **rudihawk said:**
> I didn't fix it, I have no idea what to do, basically waiting for 9.04 to come out and goin to try and install that, unless someone else can offer up another solution?

I have had this problem with Intrepid since it came out. Still waiting for a fix. I even wiped out my install and installed clean. 
You can type exit at the BusyBox prompt and it will resume a normal boot though, that's what I have been doing.

---

### Post by rudihawk on 2009-03-08
> **Tteddo said:**
> I have had this problem with Intrepid since it came out. Still waiting for a fix. I even wiped out my install and installed clean. 
You can type exit at the BusyBox prompt and it will resume a normal boot though, that's what I have been doing.

Nah, that doesn't work for me, I get dropped to the same message all over again. :(

---

### Post by dcstar on 2009-03-09
> **rudihawk said:**
> Hey all!

After installing Hardy Heron on my new PC, I am unable to boot into the OS. After grub and the orange bar bouncing backwards and forwards a couple of times, I get dropped to a busybox shell with the following displaying on the screen:
```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay =(did the system wait long enough)
-Check root = (did the system wait for the right device?)
-missing modules (cat /proc/modules ;ls /dev)

Alert /dev/disk/by-uuid/sf93855b-d3et-494e-aaba-112e764fss9 does not exist. Dropping to a shell.


```

My specs:
Intel Core i7 920
Gigabye EX58-UD5
6GB of RAM
Nvidia GTX280 1024Mb
2 X 500GB Seagate Barracudas

I have tried booting it with the following command:

all_generic_ide floppy=off irqpoll

Help anyone?

If the disk UUID actually is correct in your /etc/fstab file then you may try setting your BIOS to have a some hard disk spin-up delay before booting - it looks like things may be happening too quickly and the drive isn't ready when the kernel tries to access it.

---

### Post by rudihawk on 2009-03-13
Ok, thanks man, I'll look into the disk UUID issue as well as the HDD delay.

Its not really an architecture issue is it? (Core i7 etc)

---

### Post by Tteddo on 2009-03-13
> **rudihawk said:**
> Ok, thanks man, I'll look into the disk UUID issue as well as the HDD delay.

Its not really an architecture issue is it? (Core i7 etc)

I have it on my AMD laptop. Seems like it's all different. From what I have read it's a boot problem where one process or other gets ahead of itself under certain conditions. I have been watching this bug for awhile:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153")

---

### Post by rudihawk on 2009-03-13
Thanks for the link! Did any of the solutions posted by replies to the problem work for you?

---

### Post by Tteddo on 2009-03-13
> **rudihawk said:**
> Thanks for the link! Did any of the solutions posted by replies to the problem work for you?

No, I even formatted the partition to start from scratch. I originally upgraded from Hardy and that's when it started. There are no pre-delay settings in my Acer laptop so I couldn't try that. But I tried everything I could. Both times I started over it booted fine on the 1st boot, but not after. I wonder what's the difference.
It's kind of annoying because it's this laptop I show to my customers when I think they would switch to Ubuntu.
I am still switching about 1 a week though ;)

---

### Post by rudihawk on 2009-03-13
Haha! Thats pretty impressive. 

Well it would be nice to have this problem fixed, I've tried everything, reformatting/reinstalling, 32bit version/64bit version. Might try install Hardy and see how it goes. 

However its not super critical or anything, I would really like to be able to use my Ubuntu, but I still have my XP which serves me fine for the moment until I can get my Linux fixed!

---

### Post by rudihawk on 2009-03-21
Ok, I managed to install 64bit Intrepid in the end. Now, Ubuntu breaks the Ethernet connection. It gets disabled in the BIOS and everything forcing me to switch everything off and restart etc etc.

Anyone know how to fix this problem? (ethernet being disabled?)

---

### Post by Anthon berg on 2009-03-24
> **rudihawk said:**
> Ok, I managed to install 64bit Intrepid in the end. Now, Ubuntu breaks the Ethernet connection. It gets disabled in the BIOS and everything forcing me to switch everything off and restart etc etc.

Anyone know how to fix this problem? (ethernet being disabled?)

Hi,

I have a similar problem. Haven't checked if it gets disabled in the BIOS though. Have you tried flashing the BIOS to a newer version btw?

---

### Post by rudihawk on 2009-03-25
> **Anthon berg said:**
> Hi,

I have a similar problem. Haven't checked if it gets disabled in the BIOS though. Have you tried flashing the BIOS to a newer version btw?

No? Why should I do that? XP is like 7 Years old and runs the ethernet just fine, surely a new ubuntu should be able to do the same?

---

### Post by Anthon berg on 2009-03-25
> **rudihawk said:**
> No? Why should I do that? XP is like 7 Years old and runs the ethernet just fine, surely a new ubuntu should be able to do the same?

Maybe the BIOS is not to spec -- maybe it is to Windows spec, but slightly off w.r.t. Linux

---

### Post by Anthon berg on 2009-03-25
Btw, I tried booting Jaunty Alpha 6 from a USB stick, and the network was still dead there. Didn't try much to get it going except for *modprobe i8169*

---

### Post by rudihawk on 2009-03-28
Anyone made any progress?
I think I am going to download and install the Jaunty Beta and see if that makes a difference. If that doesn't help, then I'm going to give Fedora 10 a go.

---

### Post by rudihawk on 2009-03-29
OK, so I downloaded Fedora 10 and the Jaunty Beta (64bit) last night. First installed Fedora and it worked fine - my ethernet was working etc. 

This morning I removed it and install the Jaunty beta, everything worked perfectly - I was up and running within 15minutes - no jokes. Ethernet is working like a dream - rebooted into windows to check that it wasn't broken, and then back into Ubuntu. 

P.S Jaunty is so friggin. FAST. WOW. Now I just have to wait for it to go final! Loving it so far!

---

### Post by Anthon berg on 2009-03-31
Nice! Thanks for the info

---

