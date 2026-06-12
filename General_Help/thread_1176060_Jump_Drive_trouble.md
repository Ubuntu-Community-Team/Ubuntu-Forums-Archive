---
title: "Jump Drive trouble"
date: 2009-06-01
forum: General Help
---

### Post by MetalTroubadour on 2009-06-01
When I try to use my jump drive all I can do is view the files on it and copy them off of it, but I need to be able to put files on the jump drive.  I've read many similar cases on the forums, and noticed that it is a permission problem and that I need to change the permissions.  But I also read that since I first used my jump drive with vista that it has windows permissions which linux is incapable changing.  I just want be able to use MY jump drive on MY computer without losing the files on it.

Please help.

---

### Post by mb_webguy on 2009-06-01
Windows completely ignores Linux file permissions, and Linux completely ignores Windows file permissions.  It doesn't matter what file permissions you've set in Windows, because Linux simply doesn't care.  A partition using NTFS or FAT32 -- the latter of which is most likely how your USB drive is formatted -- will be mounted with a given set of permissions, which will apply universally to all files and folders on the drive.

Use the command "cat /etc/fstab" to check the contents of your fstab file.  If you've booted your computer with the drive plugged in, it's possible that the system wrote an entry to fstab for the drive, and now it's using that entry (with those incorrect permissions) when it mounts the drive now.  I've that's the case, you can just delete that line from the fstab file and reboot the computer.

It's also possible that the drive has become corrupted in such a way that Linux sees it as read-only.  If that's the case, you can probably fix it by reformatting the drive.  Make sure you back up the files on the drive first, of course...

---

