---
title: "UT2004 Megapack problems"
date: 2006-07-26
forum: Gaming &amp; Leisure
---

### Post by Chris R on 2006-07-26
I got UT2004 installed and working great, and now I'm looking to patch it up so I can play online and try some mods, well, I tried the .tar.bz2 patches and ECE. With those I just threw the files into the directory after using "gksudo nautilus"

With ECE the game still worked, but with the 3369 patch the game would stop working and give me an error.

I looked around these forums and found a link to the loki megapatch .run install, I ran this in terminal and everything checked out, but when the install comes up it tells me that I need to have UT2004 installed, which is odd considering Ut2004 is installed and works well. 

Any ideas? UT2004 is one of my few options, seeing as how getting wine to work in an 64 bit enviroment is a step too far for this n00b.

---

### Post by Harleen on 2006-07-27
> **Chris R said:**
> With ECE the game still worked, but with the 3369 patch the game would stop working and give me an error.

What kind of error do you get? 
Maybe this will help you: [http://www.ubuntuforums.org/showthread.php?t=213554](http://www.ubuntuforums.org/showthread.php?t=213554)
Another common error after installing the patch is a missing "libstdc++.so.5". If UT complains about that, you can get it by installing package "libstdc++5".

I don't have a solution for your other problem yet, but let's try to solve at least the first one. ;)

---

### Post by User_Program on 2006-07-27
Try placing the files in again. The map packs first then after all the packs are in place then update to 3369. Though I think it's either updating the wrong stuff.  

If you are sure you have done everything right and it still isn't working, try installing ut2004megapack-linux.tar.bz2  you can get this from 3d gamers 
[http://www.3dgamers.com/games/unrealtourn2k4/downloads/](http://www.3dgamers.com/games/unrealtourn2k4/downloads/)    its under "files for mission packs"

I would just install this one because it will save alot of time and trouble.

That megapack has everything you need to be up to date. Minus some maps but connecting to a server and downloading them should be no problem.  

BTW that one from 3d gamers is the one I used and works great.

---

### Post by Chris R on 2006-07-27
> **Harleen said:**
> What kind of error do you get? 
Maybe this will help you: [http://www.ubuntuforums.org/showthread.php?t=213554](http://www.ubuntuforums.org/showthread.php?t=213554)
Another common error after installing the patch is a missing "libstdc++.so.5". If UT complains about that, you can get it by installing package "libstdc++5".

I don't have a solution for your other problem yet, but let's try to solve at least the first one. ;)

I got the same error as him,involving libSDL 1.2, but I have libSDL1.2Debian installed with the Synaptic package manager.

I have libstdc++5 installed, where could I get libSDL 1.2?

---

### Post by Chris R on 2006-07-27
I believe I tried the megapack .tar, but that had the same effect.

---

### Post by rs3 on 2006-08-20
I ran into this issue tonight (missing libSDL-1.2, et cetera) and found that [this thread]("http://www.ubuntuforums.org/showthread.php?t=213554") basically pointed me in the right direction, if a bit unclearly...

After you dump the patch to the appropriate directories (*gksudo nautilus* works fine, as mentioned above) you'll have two files to rename:

by default, located in /usr/local/games/ut2004/System (or wherever you chose to install ut2004, in its /System directory)

rename **ucc-bin-linux-amd64** to **ucc-bin**
and rename **ut2004-bin-linux-amd64** to **ut2004-bin**

The patch offers the 64-bit binaries separately and you need only replace the default (32-bit) binaries manually.

---

### Post by daller on 2006-09-26
Does installing the MegaPack improve single-player gaming?

...or only multiplayer?

---

### Post by Perfect Storm on 2006-09-26
Both. Especially if you play Onslaught.

---

