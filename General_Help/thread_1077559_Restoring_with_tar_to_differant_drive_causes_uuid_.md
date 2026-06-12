---
title: "Restoring with tar to differant drive causes uuid issues"
date: 2009-02-22
forum: General Help
---

### Post by sofasurfer on 2009-02-22
I saved a tar backup to the same drive that contained my operating system. Now, I did a basic install to a differant drive and then restored my tar backup to this drive, in effect creating a clone. However, on trying to boot I found the system would not boot. I got a error 15.

On investigation by reading forums, I found that the probable cause was the UUID system of drive identification. So I repeated to process but this time when I ran the restore tar command I included "--exclude=/boot". This seems to have given me a cloned system on a differant drive, just like I wanted.

This seems to be a long way around a problem. How do I restore the complete tarball, including /boot, and end up with a working system?

1) Do I need to save my /boot directories from each system so that I can restore them seperately from any tar backups if needed?

2) Or do I eliminate the UUIDs and replace them with /dev*?

3) Or do I correct my UUIDs after restoration?

4) Or none of the above?

Does the UUID for each drive change with each installation or is the UUID a permanent number that is stored in the drive and therefore can be replaced. 

In this installation my menu.lst UUIDs do not match my fstab UUIDs , and yet things are working fine. The menu.lst UUIDs are oringinal to the installation and the fstab UUIDs are from the imported tar restore file.

How confusing!!

---

### Post by sofasurfer on 2009-03-02
I think I found that I also need to exclude fstab when building a new system wit the tarball.

Are me assumptions correct? Are these two files (/boot and fstab) my problem?

---

### Post by viordiasko on 2009-03-09
> **sofasurfer said:**
> I think I found that I also need to exclude fstab when building a new system wit the tarball.
I just edit mine to reflect the changes.
```
ls -l /dev/disk/by-uuid
``` or ```
sudo blkid
```will show you something like:
```
/dev/sda1: TYPE="swap" UUID="e14799f5-84a4-4caf-a195-1e6b4226031a" 
/dev/sda2: UUID="7C2C5E8B2C5E3FF6" TYPE="ntfs" 
/dev/sda5: UUID="24e5e31e-8e02-42d0-8042-23909c9ffae0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cc5fdb19-11e9-406e-adfd-14e5e6c9ce3c" TYPE="ext3" 
```
so you can determine the new UUID's from a LiveCD before booting for the first time.

> **sofasurfer said:**
> 
Are me assumptions correct? Are these two files (/boot and fstab) my problem?
They were for me, but I tar'ed all 4 of my partitions ( /, /usr, /var, & /home ) to an entirely different PC.

I now find there are permission problems elsewhere. I can't open the network-manager (not even as root) & there are some DBus error reported as USB devices are **not** automounted. So I'm going to post a question & see if I can get it answered :) .

---

