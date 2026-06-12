---
title: "problem mounting one of NTFS disks."
date: 2009-05-17
forum: General Help
---

### Post by setrofim on 2009-05-17
I am in the process of switching to Ubuntu from Windows. I have a machine with three NTFS-formatted hard drives. Two of them (including the Windows system drive) I can mount in Dolphin without problems. The other one however refuses to mount. I've attempted to mount it in bash using
```
sudo mount -t ntfs-3g /dev/sdb1 /media/Network -o force
```However got the following:
```
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```I did as the message suggested and ran chkdsk (with /f flag) and rebooted into Windows a couple of times.  chkdsk reported no errors. I've also attempted to scan this disk by right-clicking it in Windows explorer and running the utility in the Tools tab; again, no errors. Upon rebooting into Ubuntu, I get the same error form mount command. I can use this disk Without any problems in Windows. 
I have Ubuntu 9.04 (but had the same problem with 8.10). Does anyone know what the problem might be and how it could be resolved?
Any help would be greatly appreciated.

---

