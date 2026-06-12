---
title: "Does Wubi need to install Ubuntu on a specific drive?"
date: 2009-01-12
forum: General Help
---

### Post by nerd0795 on 2009-01-12
I have recently just installed Ubuntu through Wubi on my computer's C:/.   But unfortunately there is only 20 gigs left on that partition.  There is another one consisting about 50 free gigs.  I would love to put Ubuntu on that, so I can use the last 20 gigs just for Windows and the D:/ for Ubuntu.  Is it ok to put it on another partition then what window's is installed on?

---

### Post by brandon88tube on 2009-01-12
You might be able to. If you have Windows XP just edit the boot.ini line containing wubi to this ```
d:\wubildr.mbr="Ubuntu"
```Then try moving the Ubuntu folder to the root of your D: drive just like it is on the C: drive. Also move the wubildr and wubildr.mbr to the D: drive.

---

### Post by nerd0795 on 2009-01-12
> **brandon88tube said:**
> You might be able to. If you have Windows XP just edit the boot.ini line containing wubi to this ```
d:\wubildr.mbr="Ubuntu"
```Then try moving the Ubuntu folder to the root of your D: drive just like it is on the C: drive. Also move the wubildr and wubildr.mbr to the D: drive.

Uhh.. that seems complicated...  Why can't I just choose D: when installing?  Instead of C:

EDIT:  I forgot to mention I'm running Windows Vista.

---

### Post by brandon88tube on 2009-01-12
You can, but I thought you had it already installed on the drive.

---

### Post by nerd0795 on 2009-01-12
> **brandon88tube said:**
> You can, but I thought you had it already installed on the drive.

Oops.  I meant I uninstalled it due to that fact.  Then I thought what if I could install it on D:/  So I asked it.  I WANT UBUNTU BACK :(

EDIT:  So I can just go pick D:/?

---

### Post by brandon88tube on 2009-01-12
> **nerd0795 said:**
> Oops.  I meant I uninstalled it due to that fact.  Then I thought what if I could install it on D:/  So I asked it.  I WANT UBUNTU BACK :(

EDIT:  So I can just go pick D:/?

Well there is no getting Ubuntu back once you deleted it, but if you are reinstalling you can just select the drive you want at the installation screen where it asks for size, username, etc.

---

### Post by nerd0795 on 2009-01-12
> **brandon88tube said:**
> Well there is no getting Ubuntu back once you deleted it, but if you are reinstalling you can just select the drive you want at the installation screen where it asks for size, username, etc.

Yea, good thing I kept the ISO file XD

---

