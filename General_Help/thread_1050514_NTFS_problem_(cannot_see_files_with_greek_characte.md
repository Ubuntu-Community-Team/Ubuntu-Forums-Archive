---
title: "NTFS problem (cannot see files with greek characters)"
date: 2009-01-25
forum: General Help
---

### Post by Sigur on 2009-01-25
Hello,
A friend of mine has an external hard drive with files named both in English and Greek. The files named in English are displayed without a problem. The ones with Greek are not appearing at all! As if they don't exist.
Do you have any idea why this is happening?

The strange thing is that files named in Greek existing in the internal hard drive CAN be seen and opened normally.

The external drive of my friend is NTFS, which could be the cause of the problem. But how can I solve it? Doing a format is not a good option...

(FYI: Windows XP can read all files)

---

### Post by dcstar on 2009-01-25
> **Sigur said:**
> Hello,
A friend of mine has an external hard drive with files named both in English and Greek. The files named in English are displayed without a problem. The ones with Greek are not appearing at all! As if they don't exist.
Do you have any idea why this is happening?

The strange thing is that files named in Greek existing in the internal hard drive CAN be seen and opened normally.
........

I believe there are character set options that you can use to mount the disk if the default one don't work correctly, you should be able to find something that has a solution with a bit of time searching.

---

### Post by Sigur on 2009-01-25
Thanks, it may work!! I'll try that ;)

---

### Post by Sigur on 2009-02-10
I tried using some guides from different fora about this problem with no luck. For example I used the file ntfs-3g and used the following code:

```
#!/bin/bash
/bin/ntfs-3g $1 "$2" -o locale=en_US.UTF-8,el_GR.UTF-8,$4 
```

I also used symbolic links for booting time. Nada.
Maybe I am doing something wrong there. Any other ideas?

---

### Post by KeyserSoze93 on 2009-02-10
I had the same problem (with greek chars, in fact). Run:
```
sudo blkid
``` to find the UUID of the drive (this step is optional, but is highly recommended.

Then:
```
sudo mkdir /media/usbhdd
```

Then, add the following line to fstab:
```
DriveID /media/usbhdd ntfs-3g defaults,noauto,locale=en_GB.UTF-8 0 1
```
Where DriveID is either the drive's device file (/dev/sdx), or UUID= followed by the UUID.

---

### Post by blackgr on 2009-02-10
Hey pal. try using el_GR.ISO-8859-7 instead

---

### Post by Sigur on 2009-04-24
Thanks for the feedback. Unfortunately it did not work. But today my friend upgraded to 9.04 and the problem is resolved. 
:)

---

