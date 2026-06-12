---
title: "Doom 3 Installation Problems"
date: 2007-10-13
forum: Gaming &amp; Leisure
---

### Post by benjamink on 2007-10-13
Hi everyone, I have read the info on how to install doom3 but have come across a problem. I moved all the data needed to /usr/local/games/doom3/base and /usr/local/games/doom3/d3xp, downloaded the doom3-xxxxxxx.run file from the id torrent site, ran it by doing a "sudo sh ./doom3-xxxxx.run" from the directory its located in, and this is what i get:
ben@desktop:~$ sudo sh ./doom3-linux-1.3.1.1304.x86.run 

Verifying archive integrity... All good.
Uncompressing DOOM 3.............................................................................................
./setup.sh: 279: /home/ben/.setup28695: not found
./setup.sh: 290: /home/ben/.setup28695: not found
ben@desktop~$ 

Any Ideas? This is really frustrating!

---

### Post by Sockerdrickan on 2007-10-13
First there's no need for ./
and, are you running 64bit?

---

### Post by DoktorSeven on 2007-10-13
Run it as 
**sudo bash doom3-linux-1.3.1.1304.x86.run **

Stupidly, sh is linked to a bash workalike called dash that causes problems running scripts.  

This is my continued plea for Ubuntu to remove dash.  Please.

---

