---
title: "Steam under Wine?"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by blackbeard on 2007-07-16
I am having trouble running the "SteamInstall.msi" file under wine. I don't think wine recognizes the ".msi" filetype. Any Ideas? Help is much appreciated.

---

### Post by Ripfox on 2007-07-16
I just installed wine doors, and it installed steam from the menu perfectly...no hassles. Huh. What's going on with my luck with wine lately? I was playing Deus Ex perfectly like all day. *knocks on wood*

---

### Post by blackbeard on 2007-07-17
Hey thanks. I have never heard of wine doors before. I will have to try it out when i get home.

---

### Post by jacksaff on 2007-07-17
msiexec /i filename
Dunno if there are any other values or overrides that need to be passed for steam but that is how you run .msi with wine.

---

### Post by 187eR on 2007-07-17
If you downloaded the MSI version of Steam installer, type 

wine msiexec /i SteamInstall.msi

that should install steam. the steaminstall.msi should be at your home folder and it should work :)

---

### Post by frodon on 2007-07-17
If you don't want to bother with msi files use the old exe file, steam will update itself when starting it anyway :
[http://downloads.transgaming.com/files/SteamInstall.exe](http://downloads.transgaming.com/files/SteamInstall.exe)

---

