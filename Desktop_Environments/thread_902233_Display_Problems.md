---
title: "Display Problems"
date: 2008-08-27
forum: Desktop Environments
---

### Post by blommethomas on 2008-08-27
I'm having 2 problems, which I suppose are related to eachother.

First:

when I start-up my ubuntu, I get a weird screen just before I get to the login screen.  Mostly I see the ubuntu color, but together with that I can see windows XP logos(which I have installed on this laptop too) all really messed up through eachother.  It's difficult to explain but I'll try to take a picture of it later on.
I guess this is related to a window manager that isn't refreshed or something

The second one is that I get a blackscreen when I logout of my account or try to switch user.  It's just like the screen receives no signal anymore.  I know ubuntu remains working as I can still hear the sound when you normally should see the login screen again.
I've seen this problem a lot in other threads over here but no solution worked for me.  One solution was to change something in /Etc/X11/gdm but I don't have that directory... 

I tried to reinstall ubuntu a few times but the problem remains.  Might this have something to do with my videocard?  Any help would be appreciated, I'm rather new to ubuntu(I used to work with gentoo) so I still need to find my way through it


yours,
thomas

---

### Post by overdrank on 2008-08-27
> **blommethomas said:**
> I'm having 2 problems, which I suppose are related to eachother.

First:

when I start-up my ubuntu, I get a weird screen just before I get to the login screen.  Mostly I see the ubuntu color, but together with that I can see windows XP logos(which I have installed on this laptop too) all really messed up through eachother.  It's difficult to explain but I'll try to take a picture of it later on.
I guess this is related to a window manager that isn't refreshed or something

The second one is that I get a blackscreen when I logout of my account or try to switch user.  It's just like the screen receives no signal anymore.  I know ubuntu remains working as I can still hear the sound when you normally should see the login screen again.
I've seen this problem a lot in other threads over here but no solution worked for me.  One solution was to change something in /Etc/X11/gdm but I don't have that directory... 

I tried to reinstall ubuntu a few times but the problem remains.  Might this have something to do with my videocard?  Any help would be appreciated, I'm rather new to ubuntu(I used to work with gentoo) so I still need to find my way through it


yours,
thomas

Hi and welcome, How did you install? Did you use Wubi? What is the model of the graphics card? As for switching user, instead of logging out try and just restart x with the ctrl, alt, backspace keys.

---

### Post by Buntu Bunny on 2008-08-27
> **blommethomas said:**
> The second one is that I get a blackscreen when I logout of my account or try to switch user.  It's just like the screen receives no signal anymore.  I know ubuntu remains working as I can still hear the sound when you normally should see the login screen again.
I've seen this problem a lot in other threads over here but no solution worked for me.......  


Thomas, I'm having the same problem when I switch users.  What threads did you find solutions in? I don't seem to be using the correct search terms because I can't find any answers.

---

### Post by blommethomas on 2008-08-28
Bunty Bunny, here you go:

for the gdm file: [http://ubuntuforums.org/archive/index.php/t-724723.html](http://ubuntuforums.org/archive/index.php/t-724723.html)
for the second, I don't find the thread back
but you had to disable onboard video card in your BIOS


overdrank,

I don't know Wubi so I guess I didn't use it :P  I used an ubuntu live cd to install and just upgraded to the newest version later on.

graphics card:
VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)


CTRL ALT DEL just brings me to the normal shutdown screen where I can choose between logout, switch user, shutdown...  Or did you meant something else?

---

### Post by overdrank on 2008-08-28
> **blommethomas said:**
> Bunty Bunny, here you go:

for the gdm file: [http://ubuntuforums.org/archive/index.php/t-724723.html](http://ubuntuforums.org/archive/index.php/t-724723.html)
for the second, I don't find the thread back
but you had to disable onboard video card in your BIOS


overdrank,

I don't know Wubi so I guess I didn't use it :P  I used an ubuntu live cd to install and just upgraded to the newest version later on.

graphics card:
VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)


CTRL ALT DEL just brings me to the normal shutdown screen where I can choose between logout, switch user, shutdown...  Or did you meant something else?

Hi and you kinda threw me a curve in your first post saying you saw windows along with the ubuntu colors. But the VIA graphics are not supported very well and you may try this command using the alt, F2 keys 
```
gksu displayconfig-gtk
``` you can adjust graphics driver and resolution. If it fails always remember to use the recovery mode and the xfix option to repair your graphics.

---

