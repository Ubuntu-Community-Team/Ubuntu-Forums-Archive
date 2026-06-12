---
title: "HOWTO customize the Computer from Menu"
date: 2006-07-09
forum: Desktop Environments
---

### Post by yuv on 2006-07-09
I have one ntfs partition mounted on a Dapper with write support as /media/hds5 (see HOWTO in ubuntuforums.org/showthread.php?t=142481) 

First, I would like to have the possibility to make a double click in Computer from the Computer Menu and to open the ntfs partition with write support (I am thinking to a possibility to change the desktop configuration file for that).

Second, I would like to remove a useless link to ... partition and than to rename "Filesystem" link from the same Computer - File Browser from Computer Menu.

Is there a way or any possibility?

Many thanks in advance :)

---

### Post by yuv on 2006-07-11
I still hope that somebody could give me a hint..

---

### Post by yuv on 2006-07-18
.. I am loosing my hope..

---

### Post by neoeden on 2006-07-18
NTFS write support is rather skechy, and experimental last time I checked. You can get FAT32 read/write working, but only read on NTFS. They are working on it, but it's a closed format and all.

Sorry to break the news to you.

---

### Post by yuv on 2006-07-28
> **neoeden said:**
> NTFS write support is rather skechy, and experimental last time I checked. You can get FAT32 read/write working, but only read on NTFS. They are working on it, but it's a closed format and all.

Sorry to break the news to you.

GOOD NEWS: I found ntfs-3g (see [http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710))

So, now I can make a double click in Computer from the Computer Menu to open the ntfs partition with write support! :)

Still remain the question HOWTO remove/ hide a link from Computer Menu:?:

---

### Post by HAARP on 2006-07-28
Sometimes drives which are being mounted don't get "registered" with the GUI and are not shown on the Desktop / Computer
The only way I know is to add that drive to the fstab and reboot. That should get your drive to show up

---

