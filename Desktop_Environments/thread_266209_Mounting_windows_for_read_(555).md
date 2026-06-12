---
title: "Mounting windows for read (555)"
date: 2006-09-27
forum: Desktop Environments
---

### Post by ealwen on 2006-09-27
Ok I am having some trouble mounting a couple NTFS drives.  One is a USB drive and one is another partition on the same drive.  Both are NTFS but when I am under my normal user account I get an error that I don't have permissions to view the drive. If I login as root they both work, BUT I can't change the permissions on the drive.  Under root if I try to change the permissions to make it readable to normal users I get an error about "unable to change permissions".  I would really like to just be able to read the drives under my normal user account instead of having to login as root all the time just to get access.  Please help anyone.

---

### Post by ealwen on 2006-09-27
/bump

---

### Post by enopepsoo on 2006-09-27
you should change your fstab to show that the drives have read access.:KS

---

### Post by ealwen on 2006-09-30
Yeah, I set fstab for the drives to be "ro" but I still can't change the rights to be 555.  They will only mount as 500.

---

### Post by darundal on 2006-09-30
Anyone here know how I would set up a seperate sata hard drive (with NTFS) to be readable in teh linux?

---

