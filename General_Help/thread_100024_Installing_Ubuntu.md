---
title: "Installing Ubuntu"
date: 2005-12-06
forum: General Help
---

### Post by soup440 on 2005-12-06
Hi i am installing Ubuntu on a system with Windows XP installed. I partitioned my disks to have about 170GB on Windows and 80GB for Ubuntu. I formatted my drive and installed Windows first, then tried to install Ubuntu, but I can't seem to get it to install into the other partition I set for it earlier. I don't care if I have to reinstall windows and stuff. Thanks!

Also, I have a Sound Blaster Audigy 2 PCI card that needs to use sound, but my MoBo has integrated sound, so I need to install the drivers for that, however I only have Windows drivers. I would also like to try and install photoshop (all of creative suite 2), but I know I need to use WINE for that, any help on this would be appreciated. 

What is a general location where I can find all sorts of general drivers, if there is one? Thanks, I know I'm a total linux newbie.

---

### Post by matthewv on 2005-12-06
Ubuntu needs at least two partitions, a swap partition and a / partition. It would probably be best if you open the ubuntu paritioner in the install, delete the partition you created for ubuntu, then tell ubuntu to use the unpartitioned, free space on the drive. It will then create the necessary partitions, and install to them. 

With regards to drivers, try it first (live cd, maybe) and see if it works, cause ubuntu has a lot of drivers on here. Post here with details if it don't work.

For wine, follow the debian instructions on [www.winehq.org](www.winehq.org) and you should be all set

---

### Post by Bachstelze on 2005-12-06
Ant it is also highly reccomended to create a third partition for your /home directory. If you have 80 GB, I would recommend 20 GB for /, 2 GB for swap and the rest for /home. The /home dir is a bit like Windows' My Documents but it's also the place where all your settings are saved. I's very useful to have it on a separate partition if you want to reinstall Ubuntu or install another distro.

---

### Post by serenity on 2005-12-06
i found it easiest to install windows first, and then i'm assuming you've already partitioned the space you want for linux?? if so i'd delete that partition so you just have unpartitioned space there and then run the ubuntu install cd and when you get to the partitioning part choose the 'install into largest unpartitioned space' option, and it'll auto-partition it with a swap partion and a '/' partition, and also install GRUB boot manager which will let you choose Ubuntu or Windows at startup

i'm sure there's other ways to set it up too, but that's what i did and it worked out great

---

### Post by soup440 on 2005-12-06
Thanks...I've never got such a prompt answer either!

Will ubuntu automatically install a dual-booting system? If not, what do I do?

---

### Post by matthewv on 2005-12-06
It should. It will ask you where to install the grub bootloader, and, provided it lists Windows XP, you should be fine installing the bootloader to the default location (MBR). Me... I'm paranoid about touching my mbr, so I installed it to floppy ;)

---

### Post by Bachstelze on 2005-12-06
If you have windows already installed, yes, Ubuntu will detect it and install GRUB with the Windows boot option.

---

### Post by soup440 on 2005-12-06
Thanks a bunch you guys!

---

