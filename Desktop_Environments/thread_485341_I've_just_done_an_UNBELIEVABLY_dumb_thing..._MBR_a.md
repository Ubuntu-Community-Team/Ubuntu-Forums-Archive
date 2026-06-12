---
title: "I've just done an UNBELIEVABLY dumb thing... MBR and filesystem help please =("
date: 2007-06-26
forum: Desktop Environments
---

### Post by hoppipolla on 2007-06-26
[RIGHT]**just realized this somehow got posted in the wrong section - i was sure i selected general help.  can it be moved?  Ugh this seriously isn't my day... lol**[/RIGHT]


ok, you are going to think i'm really stupid but it really was just one brief slip on the keyboard and lapse in concentration but with pretty major effects :(

See, I was trying to put Damn Small Linux on my mp3 player and to do so two of the commands you need to execute are:

** ms-sys -s /dev/sdb**

to do the MBR

**and then you run cfdisk and make it bootable, check stuff etc.**

but i was really silly, i forgot that, whilst on my desktop /dev/sda is the USB player, on my laptop sda is the HARD DRIVE(!) and sdb is therefore the player.

so what did i do?

**I've overwritten my laptop hard drive's MBR with the first command and if that wasn't bad enough, in cfdisk I fiddled with the Filesystem option twice**, once to change it to fat32 as i thought i was altering the Mp3 player, and once then to change it back to "linux" when i realized what i'd done, but of course i couldn't change it to ext3 as that isn't an option.


:( :( :( :( :( :(

so - what do i do?  i take it the MBR can be sorted from within a live cd distro somehow? but what on Earth does cfdisk do when you tell it to change the filesystem on there? it doesn't format or anything of course but what does it do? does anyone know?

is it recoverable? or do i have a major reinstallation project on my hands?

thanks guys, if there is a simple solution i will be forever in your debt :D

thanks! i am usually very good with keeping installations together, i mean this ubuntu install has been up and down and customized tons and has pulled through, but i think this might finish it off ._.

---

### Post by mysticrider92 on 2007-06-26
That is somewhat unusual... First, no cfdisk will not (afaik) format the partition, it will only set a partition table. You have to manually run mke2fs to format a partition as Ext2. The partition table could have been messed up though, which will obviously cause some problems.

I am not completely sure, but I think you could use the live cd you used to install Ubuntu to install GRUB to the MBR (effectively wiping it and putting what should be there on it). To do this, you would boot the cd, open a teriminal, and type "sudo grub". This will give you a GRUB command line. From here, type "find /boot/grub/stage1" This will give you the partition to install grub to. Then type "root (hd*,*)", using the values from the find command in place of the '*' (most likely (hd0,0)). Then type "setup (hd0)". This will write the mbr (I think). Type "quit" to exit, reboot the computer without the cd, and hope it works.

Also, in cfdisk, there should have been a way to put the partition as ext3, I think it is code 83. To fix this, you might be able to do a "e2fsck /dev/sda" from a live cd (gparted live cd, etc). Well, good luck!

---

