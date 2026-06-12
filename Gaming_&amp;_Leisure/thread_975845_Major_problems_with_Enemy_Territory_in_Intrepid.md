---
title: "Major problems with Enemy Territory in Intrepid"
date: 2008-11-08
forum: Gaming &amp; Leisure
---

### Post by nkri on 2008-11-08
I wanted to install Wolfenstein: Enemy Territory today (used it in Hardy several months ago, then removed it when I got bored), and got the .run package from [_here_]("http://files.filefront.com/et+linux+260x86run/;10389332;/fileinfo.html").  I installed it using
```
sudo sh et-linux-2.60.x86.run
```
and it seemed to go okay (no errors during installation or anything).  Then, I started it up, and everything went wrong; it showed the account setup screen for maybe a second, then all of the menus and letters turned into something really weird (I dunno how to describe it...see screenshot).  So, I uninstalled it by manually deleting the folders and symbolic links, and tried the installation again.  The same thing happened, so I grabbed the old version of ET from their website...nothing changed:(  So, now I'm looking for a .deb package or a reason for why this is happening:confused:

Any help is appreciated.  Thanks!
-nkri

---

### Post by RobOrr on 2008-11-11
Intrepid switched my graphics card driver (ATI Radeon X700) off of the restricted driver when I upgraded. Maybe it's altered which graphics driver you use? I got garbly rubbish like that when my brother tried to update my other machines drivers (he has it) and used the wrong ones.

---

### Post by MikeyUbun2 on 2008-11-11
i'm having the same problem since i updated for ALL of my games including under wine
all except armadillo run that still works :)

---

### Post by Qinkai on 2008-11-11
I installed it yesterday on intrepid using the .run file and it is runny fine for me.  Not sure why your getting the problem. Sorry

---

### Post by nkri on 2008-11-11
> **RobOrr said:**
> Intrepid switched my graphics card driver (ATI Radeon X700) off of the restricted driver when I upgraded. Maybe it's altered which graphics driver you use? I got garbly rubbish like that when my brother tried to update my other machines drivers (he has it) and used the wrong ones.

That's what I've been wondering.  The graphics driver seemed to be a problem in Hardy, and was easily changed with
```
gksu displayconfig-gtk
```
but this command doesn't work in Intrepid:(

How might you go about finding the current driver and changing it?  I have an Intel 945GM Mobile Express graphics card.

Thanks!
-nkri

PS: attached is the output of the command "et"

---

### Post by MattThLinuxNewb on 2008-11-12
Try EnvyNG and choose the driver it recommends (not always the most recent one). The gtk version is just a dummy package for the console version in Intrepid if I remember rightly, so get the qt version:
```
sudo apt-get install envyng-qt
```
Hope this is of some help, let us know how you get on.

---

### Post by Ripfox on 2008-11-12
I have had this full screen distorted problem with all my games in Intrepid as well. Don't have a clue why but if you run them as root from a terminal it doesn't happen anymore!

What is the deal with this??

---

### Post by nkri on 2008-11-12
> **MattThLinuxNewb said:**
> Try EnvyNG and choose the driver it recommends (not always the most recent one). The gtk version is just a dummy package for the console version in Intrepid if I remember rightly, so get the qt version:
```
sudo apt-get install envyng-qt
```
Hope this is of some help, let us know how you get on.

Thanks for the reply, but this package is for nVidia and ATI graphics cards and mine is Intel:(

> **Ripfox said:**
> I have had this full screen distorted problem with all my games in Intrepid as well. Don't have a clue why but if you run them as root from a terminal it doesn't happen anymore!

What is the deal with this??

Yeah, I tried running it as root before starting this thread and got the same result...good for you, though:)

So, does anyone know how to change the driver for an Intel graphics card in Intrepid?

By the way, I think the problem might lie partly in the fact that ET can't seem to find ui.mp.i386.so in ~/.etwolf/etmain.  I've tried to move that file from /usr/local/games/enemy-territory/etmain, but the output of *et* says that it wants to delete this file since it's "old."  Any ideas?

Thanks!
-nkri

---

### Post by frodon on 2008-11-13
You should post your ET log too (what you get in terminal when launching ET), it can tell us interesting things.

---

### Post by Vadi on 2008-11-13
Maybe you're missing a font it needs?

---

### Post by otchie1 on 2008-11-13
kill compliz.

I had similar grief with ETQW and ended up using a script to start it

#!/bin/bash
gksudo "X :1 -ac" &
sleep 1
nvidia-settings --load-config-only
DISPLAY=:1 /home/mark/Games/ETQW/etqw &&
sleep 2

stick that is a file, make it executable and you're away.

Also required to run things like NetBeans 4.1

---

### Post by nkri on 2008-11-13
> **frodon said:**
> You should post your ET log too (what you get in terminal when launching ET), it can tell us interesting things.

Yup, attached it in post #4:)

---

### Post by nkri on 2008-11-13
> **frodon said:**
> You should post your ET log too (what you get in terminal when launching ET), it can tell us interesting things.

Sorry, double post.

---

### Post by frodon on 2008-11-14
From you ET log it seems one .so fail to load, so delete your .etwolf foledr in your home directory and start ET, it will re-create it hopefully right this time.

---

### Post by nkri on 2008-11-14
> **otchie1 said:**
> kill compliz.

I had similar grief with ETQW and ended up using a script to start it

#!/bin/bash
gksudo "X :1 -ac" &
sleep 1
nvidia-settings --load-config-only
DISPLAY=:1 /home/mark/Games/ETQW/etqw &&
sleep 2

stick that is a file, make it executable and you're away.

Also required to run things like NetBeans 4.1

Thank you so much!  Killing compiz and then starting ET solved the problem:)  No more weird symbols or anything, just plain, readable text!  Your script didn't work for me, probably because I have an Intel graphics card, but the following commands work (assuming you use emerald):
```
metacity --replace
```
```
et
```

OK, so the problem is somewhere in Compiz, and it is stopping the game from loading /usr/local/games/enemy-territory/etmain/ui.mp.i386.so.  Think I should file a bug report about this?  The problem is present in both 0.7.8 and 0.7.9, so they would probably want it fixed before the release of 0.8, right?

Thanks!
-nkri

---

### Post by frodon on 2008-11-14
No need IMO, it's known that compiz doesn't always play well with game, it will take time for compiz to fix this.

This is why many gamers just stick with metacity for gaming.

---

