---
title: "Using WINE to play games on a different partition"
date: 2007-05-16
forum: Gaming &amp; Leisure
---

### Post by bigee1212 on 2007-05-16
is this possible? 
i have a windows partition and a linux partition, i have dibalo 2 installed on windows, is it possible to configure wine to run off the windows partition?

---

### Post by Pollywoggy on 2007-05-16
> **bigee1212 said:**
> is this possible? 
i have a windows partition and a linux partition, i have dibalo 2 installed on windows, is it possible to configure wine to run off the windows partition?

I don't know if that is possible but I have *copied* a game installed on a Windows partition to my Linux partition in order to run the game with WINE in Linux.  That was before WineX (now Cedega) came along and later made it possible to install the game in Linux.

---

### Post by Gen2ly on 2007-05-16
Yeah, Pollywoggy right thinking.  Since writing to NTFS is not safe that is the best best.

---

### Post by xzero1 on 2007-05-17
If you mean using wine to run a game installed via windows -- yes. No other install necessary, I have run quake3 and RTCW like this. Simply change to the folder and use wine to run the windows executable. A lot depends on the game and its use of dlls and need for the registry. Of course you cannot save your game or do anything that writes to the windows partition but that should make it safe to try it. My guess is few games will work though.

---

### Post by Drezliok on 2007-05-17
I run WoW from a fat32 partition, it's shared with windows.


All I did was make a launcher that pointed to the .exe and I was set.

BUT, I only run the game in Linux now, When I run it in windows it's settings get messed up.

---

### Post by general_mayhem on 2007-05-17
I run WoW from my Windows NTFS partition without problems.

NTFS read/write is *supposedly* stable now with ntfs-3g, but I have an image of the ntfs partition in case it gets borked.

---

### Post by ShadowFlar3 on 2007-05-27
The safest bet is to copy your game files to linux partition and run then from there. Allthough you can probably install almost any game with wine on linux partition, it is not necessarily in most cases, you can just copy all the files and it will run fine. Not sure about diablo2 case, though.

Also for running most games, wine will do just as good as cedega.

---

