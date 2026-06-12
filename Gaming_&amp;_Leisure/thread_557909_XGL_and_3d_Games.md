---
title: "XGL and 3d Games"
date: 2007-09-23
forum: Gaming &amp; Leisure
---

### Post by Ant_Merlin on 2007-09-23
Hello everyone, I have been searching for weeks now, trying to find a solution to 3D games working in XGL. As I am a newby I didnt realise they shouldnt work. All I kept coming back to was X86 Free DRI missing on Display 1 etc.

I have finally learnt that XGL creates an additional display at launch to run its 3D windows effects (Display 1) and if you run a program Display 1 is the default it runs with and open GL Direct rendering etc wont work. With this in mind all you need to do is tell the game to run in DISPLAY=:0 and it all works ok. No messing up trying to setup a new X server or lots of script etc (I am still learning). So what I have done is:

I created a simple script for each of my games eg Sauerbraten

> 
gksudo edit /usr/local/bin/sauerbraten

#!/bin/sh
DISPLAY=:0
/usr/games/sauerbraten

save this then:

sudo chmod a+x /usr/local/bin/sauerbraten
to make it executable.


I then edit the launcher in the games menu to this path and hey presto, the game works with direct rendering and no crashes. To prove this try:

> 

DISPLAY=:0 glxinfo
returns direct rendering on etc..

me@computer:~$ DISPLAY=:0 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2



you can also use it for testing other things like glxgears etc.

It has taken me weeks to learn this, as a total newby (only running Ubuntu for the last month or so) maybe we should make a sticky for other noobs so they dont spend weeks of searching to find an answer.

Please let me know what you experienced Ubuntu users think.

---

### Post by Ant_Merlin on 2007-09-23
Anybody out there?

---

### Post by Althares on 2007-09-23
Wait.. so it just moves it to the display for certain games, so it won't work with Wine or Cedega or anything like that?

---

### Post by Ant_Merlin on 2007-09-24
I havent done it for wine yet but it can be used for ANY program, you just need to add to existing config file or create one. Only reason I havent done it for wine yet is i am very new to linux and ubuntu and havent looked for a wine config file or the boot file location.

I will def work though, just add DISPLAY=:0 before wine runs.

---

### Post by cor2y on 2007-09-24
i have always had to boot into a regualr gnome session from xgl to play even opensource 3d accelerated games mainly because the version of opengl that is used by xgl is below the minimum to run the game even if the display is switched. Something i learned to do on my own as well.
Well thank goodness ATI opened the specs up and promised to support Composite in their next binary release, now its just a matter of who will release first a working driver that can handle both composite and 3d gaming without having to run xgl, the opensource devs or ati.

---

### Post by Ant_Merlin on 2007-09-25
Hi, I have managed to run all opensource games so far ok and they all run at playable fps but i have noticed it says open GL 1.2, is there no way to update this to newer version?

---

### Post by cor2y on 2007-09-25
not that i am aware of.
I guess a fix could be out there, i think its an XGL limit, since when its back in gnome it doesn't complain when i try to launch Freespace or Doom3.

---

