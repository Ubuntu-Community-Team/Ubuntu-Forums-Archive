---
title: "Beagle and FAT32"
date: 2005-06-20
forum: Desktop Environments
---

### Post by talkingwires on 2005-06-20
(I run Breezy, but figured this question didn't really fit into the development forum.)

I'd like to give Beagle a try, and was reading a guide to setting it up. One of the steps in the guide was to enable extended attributes in your fstab for your data partitions. I dual boot with Windows, so I keep all my data on a shared FAT32 partition. Since I doubt it supports any "extended attributes", will Beagle work with it? Or am I out of luck?

---

### Post by talkingwires on 2005-06-21
*Bump*

Does anyone know?

---

### Post by ametade on 2005-06-21
You cannot install beagle on a FAT 32 partition because it doesn't support extended atributtes wich [beagle requires](http://beaglewiki.org/Enabling_Extended_Attributes). 

You can install beagle on a Ext3 partition and access this partition on windows using [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm).

---

### Post by Dave_is_sexy on 2005-06-21
Yeah that Explore2fs isn't actually all that good - just a file browser and it takes ages too. Read only. Although, there is this........ [http://www.fs-driver.org/](http://www.fs-driver.org/) (thanks to PhilippWollermann) 

Read Read: [http://ubuntuforums.org/showthread.php?t=43272&highlight=rant](http://ubuntuforums.org/showthread.php?t=43272&highlight=rant)

You could do what I'm doing and put it on an NTFS partition made writable by Captive (see next thread)

..guess that answers my question of why i can't install onto fat32

 :smile:

---

### Post by talkingwires on 2005-06-22
[QUOTE=Dave_is_sexy]Yeah that Explore2fs isn't actually all that good - just a file browser and it takes ages too. Read only. Although, there is this........ [http://www.fs-driver.org/](http://www.fs-driver.org/) (thanks to PhilippWollermann) 

Read Read: [http://ubuntuforums.org/showthread.php?t=43272&highlight=rant](http://ubuntuforums.org/showthread.php?t=43272&highlight=rant)[/QUOTE]
Ah, that sounds like it might do the trick. Thanks!

---

