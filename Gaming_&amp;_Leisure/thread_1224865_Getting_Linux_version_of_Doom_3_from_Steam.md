---
title: "Getting Linux version of Doom 3 from Steam"
date: 2009-07-27
forum: Gaming &amp; Leisure
---

### Post by suevy Suavae on 2009-07-27
This is something I've been looking for on-and-off for a while now and haven't found much, which is less then comforting. I purchased Doom 3 on Steam a while ago (when I still had Windows) and greatly enjoyed it. Now that I have Ubuntu, I've managed to get it working really well in Wine, but am constantly nagged by the fact I'm not playing the Linux version on my Linux computer. So, my question is, is there any way to prove through steam that I own Doom 3, and maybe download the Linux version of it?

I do see some reasons they might not allow this, but I was hoping maybe someone here knew something I didn't.

---

### Post by noerrorsfound on 2009-07-27
Steam doesn't offer a native Linux version for download, but you should be able to use the normal Linux installer and copy the pk4 files from where the Windows version is installed.

[ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run](ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run)

I'm not sure how Steam handles Doom 3's CD key but check the game's folder for a file called "doomkey" which should be in the same place as the pk4s.

---

### Post by ELD on 2009-07-28
The CDKey should be in a file in either the steam directory or the installed doom3 directory.

noerrorsfound is right, you can use the linux installer with files copyed over from your install.

---

### Post by suevy Suavae on 2009-07-28
Thanks guys!

Between your advice and [this site]("http://www.blog.highub.com/linux/install-run-and-play-doom-3-on-ubuntu/"), it wasn't too bad. Now I have to make it recognize the CD key, though worst case I could just write it down and insert in manually.

---

### Post by dusanyu on 2009-07-31
if you have acess to the Windows install of Doom 3 on a drive you need to navigate to the file were it is installed on your windows Machine. in that file you will fond a folder named /base 

in that folder you will find these files (i am also including the Hashes for these file in the list) 
71b8d37b2444d3d86a36fd61783844fe  base/pak000.pk4
4bc4f3ba04ec2b4f4837be40e840a3c1  base/pak001.pk4
fa84069e9642ad9aa4b49624150cc345  base/pak002.pk4
f22d8464997924e4913e467e7d62d5fe  base/pak003.pk4
38561a3c73f93f2e6fd31abf1d4e9102  base/pak004.pk4

also while pokeing around \base in windows look for the files "doomkey" and "xpkey" (these should have your Doom3 CD key instide)

burn these to a DVD

next go to id's ftp server and grab the linux installer
[ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)

after you run the installer copy the pak files you burned to 
/usr/local/games/doom3/base

first launch will ask for your key enter it 

Good Luck

---

### Post by suevy Suavae on 2009-07-31
OK, I thought I had beaten this, but it just keeps going. I have the two keys (doomkey and xpkey), but I'm not sure why I'm burning them to a cd. It has also come to my attention that the retail version of Doom 3 has an 18 (I believe) character cd key, but the ones you get from steam are only 17. However (this is where it gets really good), I can't verify this because the two keys I have are only 16 characters.

I have I feeling this is doable, but it seems to be going out of it's way to make it hard.

P.S. It's not a huge problem if this doesn't work because, as I mentioned earlier, I do have it running in Steam with Wine, I would just prefer the native Linux version.

Oh, I forgot to mention, I have gotten the game to start with the id screen, then it asks for my cd key, and neither of the two I have work (the key it wants has a space for two characters that are separate from the others, but I don't see one divided like that).

---

### Post by Rumbl3 on 2009-08-01
sry to hijack for a moment just curious if people still play doom 3 online? (tend to be a multiplayer gamer only :)

---

### Post by suevy Suavae on 2009-08-01
To my knowledge they do, though I haven't played on line in a while, so I can't be positive.

---

### Post by japboy on 2009-11-04
i suppose Doom3 Steam version binary uses "STEAM_doomkey" and "STEAM_xpkey" instead of "doomkey" and "xpkey", and Steam automatically generates correct keys into the files every time we launch the game through Steam. maybe that's why "STEAM_***" files include letters "%CDKEY%" something like a programming variable.

i actually got same problem. id like to run Doom3 and RoE on Ubuntu with native binaries from idstuff. is there any way to check the keys on Steam client?

---

### Post by stevefed5291 on 2010-03-09
I realize this thread is over a year old but I found a workaround that will let you play without the cd key. Before you scream 'warez' let me finish. It will not help anyone play the game without purchasing the retail version from somewhere as you do still need the pk4's, it will only help people that have purchased the game legitimately but can't play it on Linux due to discrepancies in the length of your cd key. idSoftware is the only big game company I know of that actually ports their games to Linux, and as such you should buy their product to support them. Now...

When you get to the screen where it prompts you for a cd key, you can ~ into the console and load any map you want, such as:

map game/delta4

the map command looks for a map in the maps folder (inside one of the pk4's), then goes into the game sub-directory and loads delta4.map. The same applies for doom mods, but you'll have to open their pk4's and see where the maps are saved. I know the inhell mod just has them all in the root of the maps folder so you would only enter 'map entrance' or whatever.

If anyone's still paying attention to this thread,  I hope this is of some use.

---

