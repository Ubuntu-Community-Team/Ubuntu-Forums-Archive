---
title: "doom 3 starting problem"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by DaGGer on 2007-07-21
Ok well I'm having trouble with my Doom game. Ok well I got the .paks got the installer. I installed the game, do I need to copy the .paks over to where I installed the game or what? When I go and click on the doom3 folder to launch the game it comes up with the window that asks if I want to run in terminal, just run it, or display it. Now I hit run the first time and nothing happened. then I clicked run in terminal and I see open a terminal but nothing gets displayed and it shuts the terminal before I can see anything on it.

---

### Post by dorath on 2007-07-21
According to the installation instructions [here]("http://zerowing.idsoftware.com/linux/doom/"), you do need to copy the pak files after you run the installer.

> The following files need to be copied from the win32 install CDs
to your base/ directory ( md5 sums provided below as reference )
by default, /usr/local/games/doom3/base

71b8d37b2444d3d86a36fd61783844fe  base/pak000.pk4
4bc4f3ba04ec2b4f4837be40e840a3c1  base/pak001.pk4
fa84069e9642ad9aa4b49624150cc345  base/pak002.pk4
f22d8464997924e4913e467e7d62d5fe  base/pak003.pk4
38561a3c73f93f2e6fd31abf1d4e9102  base/pak004.pk4


It has been quite a while since I installed Doom 3 on my system.  I seem to remember the installer creating a couple menu items to launch the game, but they were in an odd place like under "Other" or something.  Try looking around for them, they might not show up by default either.  Sorry for being so vague there, it really was quite a while back. :-\

---

### Post by GhostZrydA on 2007-07-21
-

---

### Post by DaGGer on 2007-07-21
Ok well I didn't install to the /usr/local/games/ folder because i don't have permission. now I want to uninstall it and redo the install. how do I uninstall it, do I just delete the folders and stuff or what? I want a fresh start. I can't find an unistall thing. Also how do I gain permission so I can install it, do I need to use the "sudo nautilus" command or what.  Thanks for your help, I love this game and I really want to play it.

---

### Post by hikaricore on 2007-07-21
> **DaGGer said:**
> Ok well I didn't install to the /usr/local/games/ folder because i don't have permission. now I want to uninstall it and redo the install. how do I uninstall it, do I just delete the folders and stuff or what? I want a fresh start. I can't find an unistall thing. Also how do I gain permission so I can install it, do I need to use the "sudo nautilus" command or what.  Thanks for your help, I love this game and I really want to play it.

> 4-Then you can run the file as an executable

Quote:
sudo sh ./doom3-linux-1.3.1302.x86.run

If you follow the posted instructions you will have the proper file permissions.  This is what sudo is for.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by DaGGer on 2007-07-22
Ok well thank you. Its up and running but I don't seem to have any sound. I havn't gotten into the game to actually play it yet but I've gotten to the menu and I don't have sound. If any can help me out thats great other wise I guess I'm onto searching through the forum again.

---

