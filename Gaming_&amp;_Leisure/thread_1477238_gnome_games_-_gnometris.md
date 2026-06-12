---
title: "gnome games - gnometris"
date: 2010-05-08
forum: Gaming &amp; Leisure
---

### Post by vwbug on 2010-05-08
I have karmic on my computer. Not much of a game person but I did like the gnometris that was on Hardy. The one with this version is slow and ugly.  Anyway to put the Hardy version of gnome games on karmic?

---

### Post by efikkan on 2010-05-08
An older version of Gnometris will have conflicting dependencies with the gnome-games package. So you'll have to use grome-games and grome-games-common packages from Hardy to be able to run Gnometris from Hardy. You may try to remove the existing packages and try this, but I can't guarantee it will work.

An other alternative is to compile Gnometris yourself. Try downloading the source code, unpack it and run "make" from the folder in terminal.

BTW: Wich graphics driver and graphics card do you got?

---

### Post by pieman711 on 2010-05-09
I personally think Ltris is a much better tetris game, it has better graphics and is less glitchy than gnometris. you should be able to get it simply by typing...

sudo apt-get install ltris
then typing in your super user password 

enjoy

---

### Post by vwbug on 2010-05-09
I have an older NVIDIA card, a MX 4000 and a Optiquest CRT monitor, which is fine for what I want to do (Ubuntu 10.04 didn't like though)

I may look for a DOS version and run it under dosbox.

Thanks for the ideas.

---

