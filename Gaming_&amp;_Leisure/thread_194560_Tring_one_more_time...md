---
title: "Tring one more time.."
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by RotoGrip on 2006-06-11
Hi all,

 While trying to get AlienArena to work. im coming up on this error.

Verifying archive integrity... All good.
Uncompressing Alien Arena 2006: Uranium Edition for Linux..........................................................................................
gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error

/home/jeff/.setup7794: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Its been nothing but problems since the upgrade to Dapper, If i cant get this to work then ill move onto another distro. Tired of playing hell just to get somthing to work in this Distro anymore.

Thankyou

---

### Post by seth0x2b on 2006-06-11
Every distro needs tweaking.It's not the distro that has problems, but the general applications that you/we have installed.
First of all, it seems you are missing the gtk 1.2 libs(Dapper has GTK 2.0).That's no problem, just fire up a terminal and:
```
sudo apt-get install libgtk1.2 libgtk1.2-dev 
``` It's sure easier than changing to another distro.

The crc error might mean that the installer is eighter corrupted or incomplete.You mights try to download it again

Cheers

---

### Post by RotoGrip on 2006-06-11
Thanks Seth,

 Ill give it ago, as far as the crc errors i get them everytime i try to install a package. Ive done the download agin deal but they always give the that crc error. Never had that issue with Breezy.

---

