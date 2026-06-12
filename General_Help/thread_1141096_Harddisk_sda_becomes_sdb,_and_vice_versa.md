---
title: "Harddisk sda becomes sdb, and vice versa"
date: 2009-04-28
forum: General Help
---

### Post by Milleman on 2009-04-28
Hi,

Could someone please tell me how to prevent my 20 GB HDD and my 80 GB HDD to occasionally swap (interchange) their device names after reboot? Sometimes the sda becomes sdb and vice versa.

Help!

/Mill

---

### Post by Titan8990 on 2009-04-28
udev rules: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by kpkeerthi on 2009-04-28
> **Milleman said:**
> Hi,

Could someone please tell me how to prevent my 20 GB HDD and my 80 GB HDD to occasionally swap (interchange) their device names after reboot? Sometimes the sda becomes sdb and vice versa.

Help!

/Mill

Are these external? How are you mounting them? Using FSTAB?

---

### Post by kpkeerthi on 2009-04-28
UDEV would possibly name the device differently each time. You should use [UUID]("https://help.ubuntu.com/community/UsingUUID") to refer to the partitions if you are mounting using [/etc/fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Milleman on 2009-04-28
> **Titan8990 said:**
> udev rules: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

Thanks for the link, but both my harddisks are SATA and uses the internal SATA controller on the mainboard. The tutorial on the link only covers USB harddisks (which is also very interesting information, but doesn't help me right now) :(

---

### Post by Milleman on 2009-04-28
> **kpkeerthi said:**
> UDEV would possibly name the device differently each time. You should use [UUID]("https://help.ubuntu.com/community/UsingUUID") to refer to the partitions if you are mounting using [/etc/fstab]("https://help.ubuntu.com/community/Fstab")

That sounds like something in the right direction. Do you have a clue, link or tutorial that describes how to use the UUID in fstab? :)

BTW...
The 80 GB drive is not supposed to be mounted after boot. Only the 20 GB is to be mounted and booted on. The drives should keep their device names as static every time the computer is booted. I would prefer the 20 GB boot drive to have the device name "sda" and the 80 GB drive to have the device name "sdb".

---

### Post by Titan8990 on 2009-04-28
that guide is specifically for usb but the same concept can be applied to internal drives.

---

### Post by kpkeerthi on 2009-04-28
The links are right there in my post

---

### Post by Milleman on 2009-04-28
> **kpkeerthi said:**
> The links are right there in my post

Thanx! Realized that after I posted! :)

I've now got a grip on how UUID and fstab works. But if I want the sdb1 drive (80 gb) to always be sdb1 without enter it into the fstab (I don't want i mounted during boot)... How do I make that clear for the system?

---

### Post by coffeecat on 2009-04-28
As I understand it, sda and sdb are device nodes created by the kernel long before (well - milliseconds before) fstab is read and before udev kicks in. They are derived from how the BIOS is reading your hard drives, or to which SATA connectors on the motherboard they are attached. So - BIOS first disk becomes sda and so on. fstab doesn't designate which drive is sda, nor does udev.

If sda and sdb are swapping around, then something odd must be going on in your BIOS.

---

### Post by Milleman on 2009-04-28
> **coffeecat said:**
> As I understand it, sda and sdb are device nodes created by the kernel long before (well - milliseconds before) fstab is read and before udev kicks in. They are derived from how the BIOS is reading your hard drives, or to which SATA connectors on the motherboard they are attached. So - BIOS first disk becomes sda and so on. fstab doesn't designate which drive is sda, nor does udev.

If sda and sdb are swapping around, then something odd must be going on in your BIOS.

Maybe so. I've noticed the same happening on a different PC of mine, when I used two physical harddisks. That time it nearly was a disaster, since I were about to repartition the 2nd harddisk. It then turned out that the sda and sdb was automatically swapped for some reason after boot and I formatted the wrong harddisk (with the Ubuntu live CD) with all my precious files on. Luckily I managed to recover the partition information with almost no file loss. So this is the second computer with Linux (Ubuntu) that shows this kind of behavior.

Isn't there a way to actually lock the harddisks to a static device name like hda, hdb, sda, sdb etc with regards to their physical ID or attributes, no matter if BIOS report the drive as 1st or 2nd drive?

---

### Post by Milleman on 2009-04-29
I'll guess there aren't then...

---

### Post by kpkeerthi on 2009-04-29
I don't understand what makes you so concerned about the device names being /dev/sda. 

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Milleman on 2009-04-30
Because I'm running XEN with a virtual Windows 2003 and the 80 GB is used as a 2nd harddrive to that Windows machine. If it becomes "sda" the I have to change the startup CFG file to match the device name for that Windows machine in order for Windows to see the 2nd HDD. This is very troublesome to me as I have to reboot sometimes.

Don't we just hate when people are asking "-Why do you want that"? It's like when you're at McDonalds and ask for a Big Mac without sauce. If the clerk ask you:

-Why do you want that?

Don't you get frustrated?
Just please, with sugar on top, give me a Big Mac without sauce!

People always got their reasons. If there's a solution, please provide it. If not, just say it can't be done. If there's an alternative, I'm open ears!

/Mill

---

### Post by mixmaster on 2009-04-30
> **Milleman said:**
> Don't we just hate when people are asking "-Why do you want that"? It's like when you're at McDonalds and ask for a Big Mac without sauce. If the clerk ask you: "-Why do you want that"... Don't you get frustrated?

People always got their reasons. If there's a solution, please provide it. If not, just say it can't be done. If there's an alternative, I'm open ears!

/Mill
"Why do you want it?" is a perfectly reasonable question, as it frequently allows the questioner to suggest a completely different approach to the problem.

---

### Post by Milleman on 2009-04-30
Are we into semantics? :)

---

### Post by duane-tech on 2009-05-04
Include the "noauto" option in fstab to prevent a disk from being mounted a boot.

---

### Post by Milleman on 2009-05-17
> **duane-tech said:**
> Include the "noauto" option in fstab to prevent a disk from being mounted a boot.

Thank you! ):P

---

