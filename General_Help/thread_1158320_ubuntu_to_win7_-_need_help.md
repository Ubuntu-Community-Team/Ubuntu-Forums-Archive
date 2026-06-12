---
title: "ubuntu to win7 - need help"
date: 2009-05-13
forum: General Help
---

### Post by mrzubi on 2009-05-13
Hey all,

I am sick of running steam in wine and I want to install the windows 7 RC. I am not dual booting. My machine is currently ubuntu only.

Can i simply download the win7 iso, boot from cd and install windows?

Will i run into problems with my ext3 filesystem, or will windows see and reformat my whole drive for me? (I dont want to have to use gparted if i dont have to)

---

### Post by prem1er on 2009-05-13
Are you trying to remove Ubuntu completely?

---

### Post by pennacook on 2009-05-13
win7 should just format and go, but you would probably be wise to clean up the partition table with gpartd beforehand.

---

### Post by mrzubi on 2009-05-13
> **prem1er said:**
> Are you trying to remove Ubuntu completely?

At the moment I am, yes.

---

### Post by mrzubi on 2009-05-13
> **pennacook said:**
> win7 should just format and go, but you would probably be wise to clean up the partition table with gpartd beforehand.

If I used gpartd should I reformat my whole HD to NTFS? OR does windows 7 use a different filesystem...

---

### Post by Tipped OuT on 2009-05-13
No, Windows 7 uses NTFS, and format the whole drive that way, if you're planning on getting rid of Ubuntu entirely.

---

### Post by mrzubi on 2009-05-13
thank you tipped out.

I guess my final question is:

Will the Windows 7 installer give me the option to entirely reformat my HD to NTFS or should I just use gpartd?

 (you might have already answered this sry)

---

### Post by stathol on 2009-05-13
If it's anything like previous versions of Windows, the installer should give you the option of deleting the existing "foreign" partition(s). You can then create a new partition and format it NTFS. Other than having to jump through a "yes, I really mean to delete this partition and destroy all my data" hoop, it should work fine. I don't really see any reason to repartition it with gparted first.

---

### Post by Cheesemill on 2009-05-13
I'd let Windows do it for you. You could create a single partition first but I'm pretty sure the Windows installer would have to change this anyway. Windows 7 creates 2 partitions upon install, a boot partition and an install one.

Cheesemill

---

### Post by Fzang on 2009-05-13
Windows 7 installer (as well as vista, XP and probably also previous versions) comes with its own partition tool. Just delete every partition on the harddisk and start a new, windows 7 will automatically format and create necessary partitions

I don't get why everyone wants to format with gparted thought it may be lots of fun

---

