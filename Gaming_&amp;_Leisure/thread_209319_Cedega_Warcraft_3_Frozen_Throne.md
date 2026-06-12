---
title: "Cedega Warcraft 3 Frozen Throne"
date: 2006-07-05
forum: Gaming &amp; Leisure
---

### Post by reflexion on 2006-07-05
I just installed warcraft 3 reig of chaos on cedega 5.2 and I want now to install Frozen Throne. When I put the cd in the drive and run cedega, it says that there is no warcraft3 roc installed. 

I think I have to edit user.reg:

[Software\\Blizzard Entertainment\\Warcraft III] 1115591174
"InstallPath"="C:\\Program Files\Warcraft III"

but I dont find the file.

thanks

---

### Post by reflexion on 2006-07-05
?
no help?

---

### Post by Imrik on 2006-07-07
Just make sure that when you install TFT with Cedega that you install it to the same Game Folder that you installed RoC to, otherwise the TFT installer won't detect the RoC installation.

---

### Post by jrd2 on 2006-07-11
I am having the same problem. 

You don't get a chance to install it the ROC directory as the "install" button does not show. Instead it says "Warcraft III Required - please install Warcraft III before installing Frozen Throne".


I am using the latest version of cedega UI and Engine.

thanks

J

---

### Post by jrd2 on 2006-07-11
Problem solved. Problem was caused by my own lack of understanding cedega. For others, this is how you install FT:

i) have ROC installed

1) open cedega
2) insert CD
3) click install
4) with the newer cedega versions click the "Detect Game Disk"    button
5) now for the magic part: Change the "Game Folder" from "Warcraft III The Frozen Throne" to just "Warcraft III" (or whereever you installed ROC"
6) click continue. All should be good.

---

### Post by Mr_HeNtAi on 2006-07-11
> **Imrik said:**
> Just make sure that when you install TFT with Cedega that you install it to the same Game Folder that you installed RoC to, otherwise the TFT installer won't detect the RoC installation.


I couldn't have said it better. ;)

---

