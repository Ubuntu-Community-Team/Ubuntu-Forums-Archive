---
title: "Pre installed Windows XP Installingin Ububtu"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Dutch on 2006-01-25
Hi ,

I've got a new IBM PC ( P4 3Ghz coming from 500Mhz Celeron !) it has preinstalled Windows XP wich starts installing through the net by starting up the PC.

But ! I want Ubuntu to be the main OS en want to install first Ubuntu and then XP with in Ubuntu.
So that when Ubuntu is running I can go to XP through an Linux converter.

Is that an good idea and how do I do that ?
ore should I do it an other way ??

Like to hear from u !

---

### Post by alamba on 2006-01-25
Let it go ahead and install. Post that use a live CD and run gparted. Create a empty partition. Then install ubuntu in that partition and during grub installation choose ubuntu as the default boot.

Akshay

---

### Post by Dutch on 2006-01-25
[QUOTE=alamba]Let it go ahead and install. Post that use a live CD and run gparted. Create a empty partition. Then install ubuntu in that partition and during grub installation choose ubuntu as the default boot.

Akshay[/QUOTE]

Oke quite easy thanks.
I believe I have a 80Gbyte HD.
How much should I give XP ? I only use it for some games and Word.

I've tried the live CD (version 5.04) but no gparted there ?
Probebly u meant with installing Ubuntu u can size the partitions ?

---

### Post by sayanchak on 2006-01-25
The rule you need to follow here is called **dumbest OS first**. So, first complete your XP installation. After that get a Knoppix CD friends and boot. It has qparted in it. Use qparted to create big enough root and swap partitions for Ubuntu. Reboot into XP to check if everything is in order. If XP fails to boot, dont panic, just put in the XP installation CD and you'll get a command to repair the mbr. Now go ahead with your Ubuntu installation. Everything will be just fine.

---

