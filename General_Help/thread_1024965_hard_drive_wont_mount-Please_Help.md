---
title: "hard drive wont mount-Please Help"
date: 2008-12-29
forum: General Help
---

### Post by drewm1732 on 2008-12-29
Hi, I'm trying to mount and recover some files from a crashed XP (SP2) computer using a live cd of Ubuntu 8.04. I fist had the issue where the drive didn't clean up properly and I followed the tutorial to mount it:
[http://www.howtogeek.com/howto/windo...dows-computer/](http://www.howtogeek.com/howto/windo...dows-computer/)
Problem is, it seems when I run the command "fdisk -l" that there are two identical drives named sda1 and sdb1 when I know that there is really only a single hard drive in the computer. The force mount technique in the tutorial worked for one drive (sdb1 I belive) but not the other and it appears there are no user files on the drive it did mount.
When I try the same command with sda1 I get the following error:

ntfs_attr_pread: ntfs_pread failed: Input/output error
failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the -f paramater is very important. If you have Soft/FakeRAID then you must first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the dmraid documentation for the details.

I'm using a NTFS drive and I don't know what SoftRAID/FakeRAID are but I'm almost positive the drive is not one. And I don't have a functioning version of Windows so that error message is no help at all. Has anyone run into this problem with a drive? Why is it split into two (sda1 and sdb1) and why would one mount and not the other? It's the same drive.

the command I'm using to mount is: 
mount -t ntfs-3g /dev/sda1 /media/disk -o force

---

### Post by drewm1732 on 2008-12-30
bumping up, still really need help with this

---

### Post by drewm1732 on 2008-12-30
bumping up, still really need help with this

---

### Post by OinkOink2 on 2008-12-30
EDIT - With regard to force mounting, I found the solution to this same issue here:

[http://ubuntuforums.org/showthread.php?t=694301]("http://ubuntuforums.org/showthread.php?t=694301")

But with the rest, that's above me at the moment...*sigh*

---

