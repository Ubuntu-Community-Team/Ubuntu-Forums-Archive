---
title: "Tri-Boot?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Mike_N on 2006-06-17
So... I have two hard drives in my PC, one has Windows and the other has Dapper on it. Upon install, Grub was great about writting the boot loader for me and made duel booting a sinch...

So i was thinking, if i use G-Parted and cut my 2nd drive in half, and install SUSE to the 2nd partition and then install Dapper to the first, would it be as successful in detecting the other two operating systems and setting up the MBR accordingly?

Thanks, Mike

P.S - I go the Vista Beta too but a Quad Boot System just sounds to crazy...

---

### Post by ajgreeny on 2006-06-17
If I remember correctly, Suse10 is not so friendly about other linux OS's already installed.  Make sure you keep a note of all the grub entries for ubuntu before you add suse to your machine then it's easy enough to add those entries to your grub.conf or menu.lst equivalent file on suse.
Ubuntu does it brilliantly, doesn't it?

---

### Post by Mike_N on 2006-06-17
Plan was to reformat and then install SUSE and then re-install Ubuntu as so that Ubuntu will hopefully detect the other OS's... so it should work?

---

### Post by chavo on 2006-06-17
Yes the installer will set up grub for you with the option to boot Suse as well.
And yes the Suse installer does the same thing, it will find your ubuntu install and add an entry to the boot menu.

---

### Post by Herman on 2006-06-17
It should work, if you install SuSe before you install Ubuntu so SuSe will be on Ubuntu's GRUB. I am sure SuSe uses GRUB too but I've never tried SuSe so I don't know. Someone else reported that SuSe's GRUB didn't add Ubuntu to the menu.lst, but I don't know why not. Ubuntu will probably add SuSe okay though.

Did you know you can use GRUB's Command Line Interface to find other operating systems and boot them for you manually if they aren't correctly added to the menu automatically? [*Click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to see that. It might help you.

Also, did you know that you can install a bootloader to the first sector of you Ubuntu partition as well as to MBR? (And use either one to boot with).
I had Grub installed to my MBR and Lilo installed to my first sector and used GRUB to boot with normally, but also had the option to use [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") to boot (via LiLo) in an emergency if I do something silly and disable GRUB.

Right now I have GRUB on both my MBR and also my boot block (first sector). GAG can boot Linux via either GRUB or LILO.
To install GRUB to your first sector (in addition to having it installed to MBR), first make sure you know the correct partition number for your Ubuntu (or other Linux) partition. If uncertian, use this command: ```
sudo fdisk -lu
``` to check. Then, to install GRUB to the first sector (even if you already have it on MBR), use this command, ```
sudo grub-install /dev/hda2
``` (Where hda2 is your Ubuntu partition.) (You should be able to do the same for other Linux partitions as well).
GAG Boot Manager is good to have around while you are doing Linux installs because it will always boot Windows in an emergency if there is a bootloader problem and you need to use Windows in a hurry for some reason.
I think with those extra tricks up your sleeve you will be able to cope with anything! Have fun and good luck, Regards, Herman :D

---

### Post by roger64 on 2006-06-18
I had XP and OpenSuse 10 on dual boot. Then I installed Dapper. Dapper set up its own Grub in MBR and recognizes "other exploitation systems, ie XP, OpenSuse and OpenSuse recovery. 

Works fine O:)  Don't worry. Be happy

---

