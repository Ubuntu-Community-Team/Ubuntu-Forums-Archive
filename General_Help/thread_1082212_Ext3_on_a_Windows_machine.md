---
title: "Ext3 on a Windows machine"
date: 2009-02-27
forum: General Help
---

### Post by mpc350 on 2009-02-27
Hi guys, 

I'm working with a dual boot laptop and an external firewire HDD.  I really like the ext3 file system and its advantages of journaling and resistance to fragmentation and how it is native to linux, and so have formatted my external from ntfs (it always had permissions problems with mac and ubuntu) to ext3.  I can easily get windows to use this drive using the ext2fsd drivers, but want to know if windows will "treat it" like linux will, with auto-defragmentation and journaling etc, or will windows treat it like it treats everyting else and say "to hell with your fancy FS, I'm going to arrange files the way I always do".  If that is the case would it make more sense to just go FAT32 and have a drive easily readable by mac, ubuntu, and windows, but maybe have to defrag occasionally?

Thanks, 
Matt

---

### Post by DGortze380 on 2009-02-27
.. deleted ..

---

### Post by whoop on 2009-02-27
I have nothing to back up my claims but I think extx is extx, so an extx driver will treat a file system the same way linux treats it.

As for fragmentation, ext3 will fragment no matter who or what is using it. It is more resistant than fat but it will still fragment. Even ext4 will fragment that's why it will have a online defragtool.

---

### Post by cariboo on 2009-02-27
I've been using Linux since 1998, and never found the need to defrag an ext3 drive. I've just started using ext4 so we will have to see how long it takes for the drive to be fragmented enough to notice a performance slowdown.

Jim

---

### Post by sges on 2009-03-01
> **mpc350 said:**
> Hi guys, 

I'm working with a dual boot laptop and an external firewire HDD.  I really like the ext3 file system and its advantages of journaling and resistance to fragmentation and how it is native to linux, and so have formatted my external from ntfs (it always had permissions problems with mac and ubuntu) to ext3.  I can easily get windows to use this drive using the ext2fsd drivers, but want to know if windows will "treat it" like linux will, with auto-defragmentation and journaling etc, or will windows treat it like it treats everyting else and say "to hell with your fancy FS, I'm going to arrange files the way I always do".  If that is the case would it make more sense to just go FAT32 and have a drive easily readable by mac, ubuntu, and windows, but maybe have to defrag occasionally?

Thanks, 
Matt

Not as far as I know. It will treat it as an ext2 filesystem. However I have never had permission problems  with ntfs under linux (ubuntu) except once with a windows home directory (I never investigated why, maybe it was encrypted?), never with an external hard drive. The only problem with NTFS under Linux is if windows is not shut down cleanly or the external drive is not dismounted safely, Linux will not be able to read the unclean NTFS partition. Windows has the same problem with unclean ext2/3 partitions although ext2fsd can replay an ext3 journal at startup.  

Perhaps you could post the circumstances of you permission problems with NTFS under ubuntu?

---

### Post by mpc350 on 2009-03-02
Twice in the past month I have wiped an external FW HDD and partitioned it NTFS.  I take it over to my Mac and it only has permissions to read.  Take it to my Ubuntu machine and "the permissions could not be determined"  I chown the permissions with my username and they become the property of "root", not my username and permissions are greyed out.  Take it back to the Mac, and still only have read permissions.  PITA.

So, frustrated, I take one drive and format it HFS+ for the Mac, knowing it is also usable on my Ubuntu machine.  I take the other and format it EXT3 and get the ext2Fsd drivers for my Windows machine. This 2nd drive is mainly for video editing with Vegas on windows but I want to be able to use it with the Mac and Ubuntu as well.

Really, I want both drives to have full permissions on all 3 OS's. And play well and not be fraggy and crashy.  That's all. 

Thanks, 

Matt

---

