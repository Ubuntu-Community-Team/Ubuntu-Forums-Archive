---
title: "Heretic 2 in Ubuntu Hoary"
date: 2005-09-01
forum: Gaming &amp; Leisure
---

### Post by janga on 2005-09-01
Yessss... i finally made it! I made Heretic II run in Ubuntu Hoary. (with the help from go... errh [COLOR=Blue]G[/COLOR][COLOR=Red]o[/COLOR][COLOR=DarkOrange]o[/COLOR][COLOR=Blue]g[/COLOR][COLOR=YellowGreen]l[/COLOR][COLOR=Red]e[/COLOR])
Two things before we start: Im a linux newbie and im not a native english speaker.

[COLOR=YellowGreen]Hint for newbies[/COLOR]: If you’re slow at typing like me, run [COLOR=Red]sudo nautilus[/COLOR] from the console. Then you have a filebrowser, which can access all directories/files. This is useful for copy/rename/change rights operations. For me, this is quicker than cp/rn/chmod commands in the console. However, remember that nautilus will not show hidden files/directories by default, but you can toggle this by pressing ctrl+H.

[COLOR=YellowGreen]What you need[/COLOR]:
- [Heretic II Loki CD-Rom](http://www.lokigames.com/products/heretic2/) (Windows CD should also work with the installer, but i cant approve that, since i own only the Loki CD.)
- Ubuntu Hoary machine with enabled 3d-acceleration. (Other Distros may work, too...)
This old game has pretty ridiculous hardware requirements (Pentium 166) and has a software renderer, too, for the case that you don’t own a 3D-accelerated graphics card.

[COLOR=Blue]1.Install the game.[/COLOR]
O.K. First obstacle. The installer on the CD is doesn’t work with modern Linux.    When you run it from console it says something like “couldn’t find heretic2” bin file. Do this instead: Install the game with this [Heretic II Loki Installer](ftp://sunsite.dk/mirrors/lokigames/installers/heretic2/).

[COLOR=Red]sudo sh heretic2-install-x86.run[/COLOR]

[COLOR=Blue]2. Apply patches.[/COLOR] 
Now the fun really begins.
2.1. Forget the Loki Update program. Doesn’t work. Download the patches manually from [here](ftp://sunsite.dk/mirrors/lokigames/updates/heretic2/) .
You will need those files:
2.1.1. heretic2-1.06b-x86.run or heretic2-1.06b-unified-x86.run. I don’t know the difference. I took the “unified” one.
2.1.2. Optional: heretic2-1.06b-(language)-x86.run if you want to change the ingame language. (40M file)
2.1.3. heretic2-1.06c-x86.run or heretic2-1.06c-unified-x86.run.
2.1.4. Optional: heretic2-maps-1.0.run for extra maps.
2.1.5. Very important: [This](http://icculus.org/~msphil/loki/x86/)  Version of loki_patch from icculus.org.

2.2. Patching the patches
2.2.1. Now run the patches with the argument --keep. Example:

[COLOR=Red]sudo sh heretic2-1.06b-unified-x86.run --keep[/COLOR]

This will make the patch report some errors, but it will extract the files into a folder called “heretic2-1.06b-unified-x86”.
Now copy the downloaded loki_patch file from icculus.org to /heretic2-1.06b-unified-x86/bin/Linux/x86. You have to overwrite the old file.

2.2.2. Then run the update.sh.

[COLOR=Red]cd heretic2-1.06b-unified-x86
sudo sh update.sh[/COLOR]

The patch should work without errors.

2.3. You guessed it! You have to do this with all patches you want to apply! Much work, i know...but at least you should apply the 1.06b and the 1.06c patch.

[COLOR=Blue]3. some “minor” fixes...[/COLOR]
Now the game should already start in software mode. But it crashed when i tried to turn on OpenGL.
There might be a more elegant solution, but i did it this way:

[COLOR=Red]sudo gedit[/COLOR]

In Gedit, open /home/(user)/.loki/heretic2/config.cfg and replace set gl_driver "/usr/lib/libGL.so" with set gl_driver "/usr/lib/libGL.so.1" in line 88.

Save the file and you’re done.

Alternative way: run the game with [COLOR=Red]heretic2 +set gl_driver /usr/lib/libGL.so.1[/COLOR]

[COLOR=Blue]4. Links[/COLOR]
[Old Loki Games Under New(ish) Linux](http://members.shaw.ca/dan.mckay/LokiInst.html) 
[Heretic 2 FAQ](http://faqs.lokigames.com/heretic2faq.html) 

[COLOR=Blue]5.Thanx[/COLOR]
Ubuntu for making Linux simple. Simple is good.
Ubuntu Community for being the best.
Gnome for ...errh Gnome.

---

### Post by Mishura on 2005-09-02
Interesting.  Do me a favor.. a while back I was able to get Heretic II to work in Mepis, but when I got to the "Lizardmen" level (I forget what they are called), and there is a part where you aquire the Storm Bow and jump down a good distance into water.  After that, and fighting some shark-looking things, there will be a switch under the bridge on the Right, facing the high platform from where you jumped from.  (This should be the "3rd" area in the game, the 1st being "The town", 2nd being the "Swamps".)

Push that button.  If it crashes, then you have the same problem as I did.  If not, then I'll give H2-Linux a sixth (or seventh) attempt.  Right now, I'm running H2-Win32 under Wine, which works rather well, but I'd rather use the native version.

Oh, and thanks for the informative step-by-step howto.  It's not much different that how I did it last time,  but recent attempts to get it to work with Ubuntu Hoary have been very unsucessful.  Maybe there was something that I missed.

---

### Post by janga on 2005-09-02
O.K., i will tell you when I'm that far. Today I'm going on vacation, so this could last a while... :grin:

---

### Post by janga on 2005-09-18
O.K. I played the game thruogh to the end now. I experienced some crashes at the beginnig but then I found out that it runs very stable, when i ran no further "big" programs (like azureus, amule, gaim...) in the background. It didnt crash in that scenario you described at all. Bottom line: old but cool game.

---

### Post by beeldings on 2007-03-10
Wow, I can't believe how old this thread is!  Anyway, would anyone happen to have a mirror or copies of the files listed in janga's post? I attempted to download the Loki installer referenced by janga but it is no longer available from that source.

---

### Post by beeldings on 2007-04-01
UPDATE:
**heretic2-1.06b-unified-x86.run **and **heretic2-1.06c-unified-x86.run** can be retrieved from [http://files.antlinux.com/linux/games/]("http://files.antlinux.com/linux/games/")

---

