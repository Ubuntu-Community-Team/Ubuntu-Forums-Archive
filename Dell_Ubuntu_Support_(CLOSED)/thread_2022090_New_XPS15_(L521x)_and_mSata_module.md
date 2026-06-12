---
title: "New XPS15 (L521x) and mSata module"
date: 2012-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Romu on 2012-07-10
hi there,
I have a brand new XPS15 (L521x reference), and first of all, I have to say I'm impressed as everything runs out of the box with Ubuntu 12.04, great!

The computer has a 32 GB mSata module, in other words, this is a small SSD. The problem here is I can't install Ubuntu on the mSata.

I found something on the net saying I have to change the mSata management from "Intel Smart Response" to "AHCI", and then flag the mSata to "boot". I did it.

Then at Ubuntu install time, I choose "Other" and the combobox shows well my main SSD and this mSata module, but it's impossible to choose it to install the system.

Any help would be greatly appreciated. Thanks.

---

### Post by Romu on 2012-07-12
Ok, I made it.

Here is what I did:
[INDENT]for the mSata module, in the Bios:[/INDENT]
[INDENT][INDENT]Change the mSata management to AHCI[/INDENT][/INDENT]
[INDENT][INDENT]Set the boot order to boot first on the mSata[/INDENT][/INDENT]
[INDENT]for the mSata module, in Gparted:[/INDENT]
[INDENT][INDENT]Remove all partitions[/INDENT][/INDENT]
[INDENT][INDENT]Create a new partition table[/INDENT][/INDENT]
[INDENT][INDENT]Create a new Ext4 partition[/INDENT][/INDENT]
[INDENT][INDENT]Flag as "boot"[/INDENT][/INDENT]
[INDENT]for the main SSD, in Gparted:[/INDENT]
[INDENT][INDENT]Remove the "boot" flag[/INDENT][/INDENT]

Then, reboot the PC, start the LiveCD and Ubuntu should see the mSata as a normal drive to install Ubuntu.

Finally you could install Ubuntu on the mSata, 32 GB is largelly enough to host all system and applications files

My config is:
mSata as "/"
main SSD for "/home" and Swap.

Enjoy!

---

### Post by AlexanderSoder on 2012-08-02
Is it possible to install ubuntu on the msata drive as described and keep the preinstalled windows system untouched? And let grub handle the dual boot?

---

### Post by oldfred on 2012-08-02
May depend on size of mSata?

You can break the RAID so then it is two separate drives. I do not think you have to totally reformat but have to also remove the hidden RAID meta-data on the drive. Linux sees the meta-data and says its RAID so only expects a RAID type install, but standard desktop does not include the RAID drivers.

 Intel Smart Response Technology.
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

