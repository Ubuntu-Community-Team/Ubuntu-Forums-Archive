---
title: "Playing already installed Steam games in Windows on Steam Ubuntu"
date: 2019-01-08
forum: Gaming &amp; Leisure
---

### Post by freek101 on 2019-01-08
Hi, the lack of games in Linux has always kept me from going fully Linux and throwing away Windows. 
Now that Steam has Proton and lots of games are well playable on Linux, I want to give going full Linux a genuine chance.
So I'm looking for the easiest way to make the switch. Ideally this would be simply installing Steam on Linux and then appoint in Steam the Windows game folder. 
Current situation is that Steam runs well, but it is unable to see other disks than the disk on which Steam and Linux are installed. The games are on a separate disk.
Is what I'm trying to do even possible? What would be the best practice going from Windows to Linux with a Steam library with 28 installed games?

Platforms used: Ubuntu 18.04 and Windows 10

---

### Post by oldrocker99 on 2019-01-09
Well, go to Steam/Settings. There is a Steam Play section at the bottom. I use the beta branch. Then check "Enable Steam Play for all titles."

It's a bit of a crapshoot; many games run perfectly, and some (Banished) have no sound, and some won't run at all. You just have to try.

---

### Post by CatKiller on 2019-01-09
Proton doesn't handle NTFS at all well (which is why that is hidden), and the situation where Steam is accessing the same files from both Windows and Ubuntu is likely to mess things up more.

It's best to copy those files to a Linux-native filesystem and then point Linux Steam at them if you don't want to download them again.

---

### Post by oldrocker99 on 2019-01-09
> **CatKiller said:**
> Proton doesn't handle NTFS at all well (which is why that is hidden), and the situation where Steam is accessing the same files from both Windows and Ubuntu is likely to mess things up more.

It's best to copy those files to a Linux-native filesystem and then point Linux Steam at them if you don't want to download them again.

THAT I didn't know about Proton, and you helped more then I did :(

---

### Post by freek101 on 2019-01-09
Good to know. I just ordered an extra SSD to install all the Steam games in Linux on. 
I guess next question will be how to go about with all the savegames, but let me first get things to run properly and I'll open a new thread later when and if needed. 
Thanks a lot guys!
I'll close this thread.

---

