---
title: "WoW crash after latest patch"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by Sleekfire on 2007-04-04
Hi, im new to ubuntu but i had WoW running pre patch, but at only 20 fps(opengl mode) so i went to:
[https://help.ubuntu.com/community/WorldofWarcraft#head-303a3f8f3a9903a00531578dcf974652f56d5312](https://help.ubuntu.com/community/WorldofWarcraft#head-303a3f8f3a9903a00531578dcf974652f56d5312)

for sum tweaking and did most of the tweaks except tweak #2

when i load wow now it'll show the login screen but instatly lock up.  i have the latest ati drivers and wine drivers to my knowledge, and i also set the winecfg to nt 4.0

if neone has had the same problem or know how to fix it that would be awesome

edit: also after many loading/crashing/restarting, every 15th try or so it'll run properlly

---

### Post by geekpower73 on 2007-04-04
Same problem here, WoW was running perfectly until yesterday's patch (or today for EU).

It locks up the screen/keyboard after displaying the background of the login screen. The last Wine message is something like "IsWow64Process() .... stub".
I tried setting Winecfg to Windows NT 4.0 but it didn't solve the issue.

I can still access my machine with SSH and reboot it.

ATI card and last Wine package from Ubuntu.

---

### Post by Praill on 2007-05-28
Same.

The last message output I get from wine is:
IsWow64Process

NT 4.0 worked before with a pre-compiled wine version (cant remember which). Now Im using the latest from the repos and NT 4.0 doesnt fix the problem.

Anyone?

---

### Post by Praill on 2007-05-29
I figured it out pretty quick. Wine 0.9.37 was breaking it for me (for some reason). I downgraded to 0.9.33 and everything is working great.

To downgrade if youve installed from the repos:
Open up synaptic
```
gksudo synaptic
```
Search for wine. Select wine but dont install, instead click on package-->force version while the wine package is selected. Force the version to 0.9.33. Once it downloads and installs apt-get will want you to update to the latest. To fix this just go back into synaptic, select the wine package and do package-->lock version.


Good luck.

---

### Post by ShadowFlar3 on 2007-05-31
If you are getting frequent random crashes (and you find a crash report in WoW/Error/ that says it was Error #132) you just need to add this to you config.wtf:

SET Basemip "1"

I had this problem for 2 weeks but then I checked blizz tech forums (doh!) and there it was :P

---

