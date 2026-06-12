---
title: "Disable Journaling EXT4 Xubuntu 10.10"
date: 2010-10-28
forum: Desktop Environments
---

### Post by metallica1973 on 2010-10-28
I have created a penstick and am trying to maximize performance. I want to disable journaling to decrease overhead and increase performance. I have already added things to the RAMDISK and now want to know how to disable this feature. thanks

[http://fenidik.blogspot.com/2010/03/ext4-disable-journal.html]("http://fenidik.blogspot.com/2010/03/ext4-disable-journal.html")

Will this suffice?

---

### Post by metallica1973 on 2010-11-03
I have resolve my own issues by:

[PHP  tune2fs -o journal_data_writeback /dev/sdb5
  tune2fs -O ^has_journal /dev/sdb5 
  (The above step is done with the drive unmounted, so boot from live cd, mount it then unmount it for it to work)
  e2fsck -f /dev/sdb5
  (This step is done like the above)
  dumpe2fs /dev/sdb5|more  ][/PHP]

this is how I resolve my issue.

---

### Post by oldfred on 2010-11-03
Herman had some suggestions in his install, also the EeePC has some info:

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)

---

