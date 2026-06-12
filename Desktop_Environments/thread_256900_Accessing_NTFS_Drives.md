---
title: "Accessing NTFS Drives"
date: 2006-09-13
forum: Desktop Environments
---

### Post by StrifeX on 2006-09-13
Yes I'm having trouble accessing files on my External HDD, how can I be able to write and execute from it? Is there any software that gives full compatibilty to NTFS partitions/drives?

Thanks in advance,
Strife

---

### Post by carontis on 2006-09-13
It's called wine and let you run windows programs

---

### Post by orb9220 on 2006-09-13
Wine will only run a small amount of apps that are windows applications,
You cannot run apps installed on your ntfs partition. If the program will  run with wine it has to be installed by wine in its folder structure.

ntfs partition cannot be written to by default. There is ntfs-3g program  that will allow this but is still considered experimental.

For access to Movies,pics,Music files most setup another HD as fat32 which winXP and linux can read and write too.

Wine will only run a few games and more apps but is lacking support for alot of the major apps. That is why I still have a dual-boot machine.

---

### Post by stmiller on 2006-09-13
Are you looking to read/write to the drive, as storage? That is built into the Linux kernel. Man mount, or search google for ntfs and linux. 

Wine is for executing windows (.exe) programs.

---

### Post by StrifeX on 2006-09-13
...I don't remember asking for your help on running Windows applications. I've got WineX for that. ;)

I was simply asking if I can delete, and add files to and from my NTFS HDD.

How can I get that ntfs-3g program orb? Thank's for the help so far guys...

---

### Post by orb9220 on 2006-09-13
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=3g)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

