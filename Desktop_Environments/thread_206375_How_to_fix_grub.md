---
title: "How to fix grub?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by GuitarHero on 2006-06-30
I tried to add a windows hdd to my grub boot loader and now ubuntu gets stuck on checking all file systems when it tries to boot.I can get windows to boot by editing its grub info(it says (1,0) when it needs to be (1,1)  so i can get to windows but it doesnt save this change.  Ive tried using the live cd to reconfigure grub but i havnt got it to work.  I dont understand how grub would affect my ubuntu booting.  It starts to boot, but then gets stuck.  I had ubuntu working on this computer with both hard drives in, i just could get to windows due to it not being on grub yet,  and now i cant get to ubuntu(the one i really want to use).

Please help

---

### Post by jrd on 2006-06-30
Type sudo nautilus /boot/grub/menu.lst. Then edit the file and save it.

---

### Post by GuitarHero on 2006-06-30
while using the live cd?

---

### Post by GuitarHero on 2006-06-30
I cant edit that file with the live cd because the live cd doesnt auto mount the hard drive where my ubuntu install is.  i dont know how to access my files.

---

### Post by jrd on 2006-06-30
I'm sorry I missread your post. I'm not sure if this will work but....
try to mount the hard drive while using the live cd, I guess just try mount -a. Then cd to the grub folder on that hard drive and edit it. maby it will save it then. If this is what you were already talking about I'm going to feel really stupid.

---

### Post by GuitarHero on 2006-06-30
i think thats what i need to do, i want to delete the windows part in ther grub loader to see if that lets me boot now.  But i dont know the exact code to do what you're talking about because im new to ubuntu.

---

### Post by jrd on 2006-06-30
I think```
mount -a
```will work. Or maby ```
mount dev/hda1
```(if that's the drive it's on).

---

### Post by GuitarHero on 2006-06-30
I typed mount -a and it didnt give any errors or conformations.  The sudo nautilus /boot/grub/menu.lst tells me that doesnt exist.  so either it didnt mount or im looking in the wrong place

---

### Post by GuitarHero on 2006-06-30
anyone.... im almost ready to go back to windows for good.  it may not work well, but it at least works.  i like ubuntu its just got so many problems.  i want to use it but ive already reinstalled twice for other issues and i refuse to again because i put a lot of files and programs on it this time.

---

### Post by Herman on 2006-06-30
Okay, there are lots of different ways to do what it is you are trying to do.
You said you want to learn how to edit your /boot/grub/menu/lst file by mounting your Ubuntu filesystem with the 'Desktop' Live/install CD.

First you will need to boot with your LiveCD, (of course), and then open a terminal.
(Applications, Accessories, Terminal).
Okay, then we need to find out the exact partition numbers for the filesystem you want to mount, we use the following command for that:
> sudo fdisk -lu If you can get that part doen youo can post the output here if you can, then we can make up the command we'll use to mount your filesystem.
Regards, Herman :)

---

### Post by caserio on 2006-06-30
Hi,

Post your /boot/grub/menu.lst
Did you try reinstalling grub ?

---

### Post by YourDoom123 on 2006-06-30
[QUOTE=caserio]Hi,

Post your /boot/grub/menu.lst
Did you try reinstalling grub ?[/QUOTE]

like the OP said, he can't get at menu.lst, which is his problem, and reinstalling grub didn't fix it.


what you need to do is figure out where the drive is being mounted. the easiest way to explain this is like attaching a hose to a water outlet. you have to know which outlet the hose is attached to, in order to turn it on, and get the water out. the other thing you need to know is how hard drives are labelled in linux. normal hard drives (parallel ata or pata) and even some sata drives are labelled as hdx, where x is replaced /w a letter that corresponds to the "number" of the drive. the first drive would be hda, the second hdb, etc, etc. this list doesn't just include hard drives, but also cdrom/dvd drives, etc. that are attached via an ide cable. if you have a sata drive thats not being recognized as hdx or a SCSI drive, then try it as sdx (most likely sda).
The next step is understanding partitions. I'm a bit tired, so I won't go into much detail, except to say that unlike windoze, linux, and therefore ubuntu, defaults by splitting your hard drive up into multiple sections, called partitions. Each partition holds a certain set of data. When you issue a mount command, what your doing is mounting a partition, not the hard drive itself. My hose analogy sorta falls apart here, but hopefully, your still following me. but the way that linux handles partitions is simple. A partition is labelled by its hard drive name (hda, etc.) followed by a number, which is the number of the partition itself. The first partition on a hard drive (physically speaking) is called 1, and you get the picture. I'm not sure how ubuntu partitions hard drives by default because i've always done it manually, so if someone who knows could clarify here...

anyway, if theres any part of that you didn't understand (and i'm sure there will be. i'm not that great at explaining things) please ask. i'm not sure how much knowledge you have about computers, or operating systems in general.

once your sure you understand try this in a terminal (from the livecd):

```

sudo -i
mkdir /mnt/ubuntu
mount /dev/hda1 #replace the h and a /w whatever's appropriate, and the 1 /w the partion that ubuntu is installed on
cd /mnt/ubuntu
gedit boot/grub/menu.lst

```

this is better then the earlier listed mount -a suggestion because you know exactly where your drive is being mounted (attached). anyway, once you have menu.lst open, edit it as you need, and comment out windows by putting # in front of all the lines that pertain to the windows install. if it still doesn't boot, post the contents of your menu.lst file here. good luck!

EDIT: alright, i really need to sleep... i did something VERY stupid. forgot to explain partitions, and didn't even include that info in the mount command... the whole purpose of this entire long post would have just been wasted...

---

