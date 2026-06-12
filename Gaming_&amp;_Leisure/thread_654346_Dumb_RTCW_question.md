---
title: "Dumb RTCW question"
date: 2007-12-31
forum: Gaming &amp; Leisure
---

### Post by manij on 2007-12-31
I'm trying to install native RTCW on kubuntu Dapper

I got the linux installer file "wolf-linux-1.4-full.x86.run" on my desktop.

I installed/extreacted from a windows retail cd rom with wine and copied 6 pk3 files to

/usr/local/games/wolfenstein/main

HOW do I execute the linux installer and how to run the game? Noob here. thanks for you help!

Mani

---

### Post by BreathEasy on 2007-12-31
Open a terminal. Type in the following:

cd Desktop
chmod +x wolf-linux-1.4-full.x86.run
sudo ./wolf-linux-1.4-full.x86.run

Make sure the destination for the installation is:

/usr/local/games/wolfenstein/

which is probably the default, but check anyway.

Make a note of where the symbolic links will be installed (the second path in the installer window). Once it's installed, with any luck you should just need to type **wolfsp** or **wolfmp** in the terminal and something should happen.

---

### Post by manij on 2007-12-31
Thanks, that worked

Mani

---

