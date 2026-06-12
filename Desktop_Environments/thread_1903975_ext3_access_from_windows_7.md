---
title: "ext3 access from windows 7"
date: 2012-01-03
forum: Desktop Environments
---

### Post by intelligence storm on 2012-01-03
I have an external hard USB formatted as ext3
How could I access data on from Windows 7 ??? (Read-Write)
I've tried list of programs neither one could help me :(
1-explore2fs-1.08
2-Linux_Reader
3-ext2explore-2.2.71
4-ext2ifs-0.3
5-Ext2Fsd-0.51

even while searching everyone says that it's work correctly !!
any help will be appreciated

---

### Post by Pablo Pablovski on 2012-01-03
Ext2FSD (0.51) works fine for me from Win 7 to multiple EXT3-formatted partitions on my system

Have you installed it as a service, and configured it to assign drive letters to the EXT3 drive? Right click on the tray icon (might be hidden in the systray).

---

### Post by intelligence storm on 2012-01-04
Hmmm.....I think the program (Ext2FSD) was not as a setup program but as a portable ! so i can run it immediately without installing !!! if it should be as installing program can you bring a link for downloading ?
and then can you give a step-by-step tutorial ??

---

### Post by Pablo Pablovski on 2012-01-04
Download:
[http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/)

FAQ, including installation
[http://www.ext2fsd.com/?page_id=7](http://www.ext2fsd.com/?page_id=7)

Basically, you need to d/l and run the .exe installer, then reboot.

On restart, the client runs in the systray - right click on it and you'll be able to configure drive letters, permanent or temporary mount points, install the driver as a service from the menu. 

Your USB drive can be set as a temporary mount using the client, but with a permanent drive letter.

And don't click on the "close" window control - that disables the EXT3 driver - instead, minimise the application back to the systray.

Works well in my experience - read/write is fine, not noticeably slower than NTFS.

---

