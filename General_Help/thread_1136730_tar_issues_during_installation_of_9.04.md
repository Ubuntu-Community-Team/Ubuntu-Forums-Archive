---
title: "tar issues during installation of 9.04"
date: 2009-04-25
forum: General Help
---

### Post by YoungCthulhu on 2009-04-25
I have just installed 9.04 and I made a tarfile containing my /home directory, prior to the installation, and put it on my usb portable HDD.  Prior to the install I tested the archive using the following command:
> tar -tvf "/media/Elements/backupfile"
All the files were there so I turned the HDD off and installed 9.04. Now I can't find the backup file on my portable HDD.  I have tried logging in as root, and using ls -la but to no avail.

Have I done something really silly that I have not yet realised, like inadvertently moving the archive back on to my computer's HDD and then formatting it?:confused:

Your suggestions would be appreciated.

---

### Post by hikaricore on 2009-04-25
Did you unmount the external drive or simply turn it off?
The second method is not a safe or reliable way to disconnect it.

You should always properly unmount any external drive.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by YoungCthulhu on 2009-04-28
> **hikaricore said:**
> Did you unmount the external drive or simply turn it off?
The second method is not a safe or reliable way to disconnect it.

You should always properly unmount any external drive.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Yes that's what I did all right, just turned it off :oops:.

Is there any software available that would let me retrieve old files that have been erased?  I would guess that the archive is still there on the disk.  Does Unix work like DOS, in that the FAT marks the disk space as being available for write over by just removing the first letter of the filename?

Thanks for your help, much appreciated.

---

