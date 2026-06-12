---
title: "How do I delete my Ubuntu partition? Will XP's bootloader reaffirm itself?"
date: 2009-02-21
forum: General Help
---

### Post by princerameses on 2009-02-21
I am dual booting with XP and ubuntu. I am using the grub bootloader and I'm wondering if XP will still boot up if ubuntu is gone. I may insall ubuntu or kubuntu 8.10. And if I wanted to just do that (get rid of 8.04 and get 8.10) would that be easier? And the reason I want to do this is because I am having a mouse issue where my USB mouse stops working. I have fixed this, but not instead of not working, it just goes a little clunky. Anyways I want 8.10 anyhow. thanks.

---

### Post by Panzor on 2009-02-21
You want to upgrade from 8.04 to 8.10?

If this is true, I would recommend backing up your home directory and a few files out of /etc/ (/etc/X11/xorg.conf for one) and pop in the 8.10 install CD and overwrite the 8.04 partition. It's the safest way. I see a lot of people that have problems when they just "upgrade" without a clean install.

Also, if you just overwrite your whole home directory, you may get an error about .dmrc file being ignored. This has something to do with you not owning the files (because you're a new user now). A quick fix is found [http://ubuntuforums.org/showpost.php?p=6107400&postcount=4](http://ubuntuforums.org/showpost.php?p=6107400&postcount=4) <---there.

---

### Post by doas777 on 2009-02-21
if you just want to install another ubuntu, just use the install disk to wipe the partition. 

otherwise, you can delete your ubuntu partition using windows disk managment tools. I believe the bootloader (GRUB) will remain however, because it is in the MBR, not the root partition. 

you can remove grub (if you want to) by booting off your windows install CD and entering recovery mode. then issue the ```
fixmbr 
fixboot
``` commands.


I think it would work best if you removed grub first, and then deleted the partition, that way grub isn't looking for a menu.lst file on a drive that no longer exists, if you choose to do it without using the ubuntu installers partitioner. 

good luck,

---

### Post by princerameses on 2009-02-21
How do I over-write the ubuntu pertition? Bare in mind I am dual booting and don't want to lose XP. I also need to make sure I don't mess it up so XP won't start. I don't have any XP disks. I don't know why everyone has them. I have never gotten them with any of the 4 computers I have puchased new.

---

### Post by doas777 on 2009-02-21
ok, your best bet, is to make note of the sizes/types of all your partitions so you can tell which is which when your in the partitioner.

then boot from an ubuntu install CD, for whatever version you want to install.  This guide will tell you all about the ubuntu partitioner:[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) .

when you get to the partitioning part of the ubuntu install, select manual partitioning. delete the ubuntu partition, but leave the MS one. then create a new one for ubuntu. you may seriously want to consider making a seperate home partition as well. in that case you would create 2 partitions (in the space where the old ubuntu partition was) and set one to mount to '/', and the other to mount to '/home'. ubuntu will take care of the rest.

then you will not have the old partition, grub will still be there and ready to boot either windows or intrepid. does that suit your needs?

---

