---
title: "Desktop strangeness - no mouted volumes"
date: 2019-11-19
forum: Desktop Environments
---

### Post by ubuntini2 on 2019-11-19
Hi
Really puzzled by recent desktop behaviour.
Running Ubuntu Mate 18.04 LTS.

Was experiencing desktop slowdowns - was unable to copy paste or delete files or folders.
Also double clicking a folder sometimes would not open it and if it did  the contents weren't visible, can only see spinning icon.
CPU process are normal, ie close to zero.

I rebooted and other strangeness happened.
None of my volumes are mounting on the desktop even though they are configured to using Mate tweak (attached)
Browsers and apps seem to launch ok.

Also if I go to Places in the menu all of my volumes open except for  just one, WORK_1TB (attached link) 

If I use Disks utility to check the filesystem on this external drive it suggests to repair but also warns that repairing may corrupt files. (attached link) This is my primary production volume. Before I attempt a repair I'd like to first back up important files but if I use GrSync I can see the volume but it won't open. Argh. 

[https://photos.app.goo.gl/f4Dum2r3pmasnFbWA](https://photos.app.goo.gl/f4Dum2r3pmasnFbWA)

Can any linux wizards help me figure out what is happening?
Any feedback appreciated.

---

### Post by Holger_Gehrke on 2019-11-20
The second screenshot shows that the disk is formatted with NTFS. Linux knows NTFS well enough to recognize it,  read from and write to it and to recognize if the file system is broken, but there are no tools to repair a damaged NTFS. If errors are detected, Ubuntu will mount the file system read only if at all. If your system is set up to boot both Ubuntu and Windows (dual boot) you can use Windows to check the file system, otherwise you'll have to disconnect the SSD from the Ubuntu machine and get it to a Windows machine.

Holger

---

### Post by ubuntini2 on 2019-11-20
Great info. Thanks!  Also wondering if perhaps NTFS is perhaps more prone to file, folder corruption than ext4.

---

### Post by Dave67 on 2019-11-29
Look on software for synaptic for ntfs-3g 
Once installed it should show on the desktop

---

### Post by coffeecat on 2019-11-29
> **Dave67 said:**
> Look on software for synaptic for ntfs-3g 
Once installed it should show on the desktop

The package ntfs-3g has been included in a default installation of Ubuntu for many years now. The underlying problem and the solution have already been described in this thread.

---

### Post by oldrocker99 on 2019-11-30
> **ubuntini2 said:**
> Great info. Thanks!  Also wondering if perhaps NTFS is perhaps more prone to file, folder corruption than ext4.

Oh my, yes. Every M$ OS fragments files; in other words, it tries to fill up space by putting small pieces of each file wherever they fit. This greatly slows down read times, as the drive head moves around to load a single file. This requires regular defragmentation with any M$ OS.
 
EVERY Linux OS instead saves a file in the smallest contiguous space that will hold it. This keeps the drive speedy, and there is never any need to defragment, because each file is complete on the disk, and can be read directly.

Here's a bit more detail: [https://www.pcworld.com/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html](https://www.pcworld.com/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html).

---

