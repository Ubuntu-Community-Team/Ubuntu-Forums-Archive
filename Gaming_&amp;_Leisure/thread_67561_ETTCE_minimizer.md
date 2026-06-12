---
title: "ET/TC:E minimizer"
date: 2005-09-20
forum: Gaming &amp; Leisure
---

### Post by krak on 2005-09-20
Hi,
Is it possible to minimize ET/TC:E and go back to my gnome desktop. With windows it wass possible by tool called etmin is ther such tool for linux?

---

### Post by dontpanic on 2005-09-20
i use this script in my et cfg...


|-----------cut here------------------------|
bind "9" "vstr switch"

set window "r_fullscreen 0;wait 200; vid_restart; set switch vstr fullscreen"

set fullscreen "r_fullscreen 1;wait 200; vid_restart; set switch vstr window"

set switch "vstr window"
|-----------cut here----------------------|

copy/paste it in your cfg file 
or make a new file with .cfg extension(i.e. minimizer.cfg) and put it in your .etwolf/etmain/

so in game type in console exec minimize.cfg

and press "9" <------ you can change this bind

now you can access the mouse on desktop by open the console...

sorry for my english....

---

### Post by krak on 2005-09-20
when execing this cfg i get message Unknow Command "fullscreen"

---

### Post by dontpanic on 2005-09-21
[QUOTE=krak]when execing this cfg i get message Unknow Command Fullscreen[/QUOTE]

you exec  this cfg in game by the console????


this works perfectly for me....

---

### Post by krak on 2005-09-21
yes i did type /exec m.cfg
and it says unknow command fullscreen

---

### Post by dontpanic on 2005-09-21
you copied this file in .etwolf/etmain?

you exec the file(if the file is called minimize.cfg) with "/exec minimize" or 
"/exec minimize.cfg" ???

---

### Post by krak on 2005-09-21
ok i have made an error by pasting it to my cfg i did
set window "r_fullscreen 0;wait 200; vid_restart; set switch vstr 
fullscreen"

but it should be 
set window "r_fullscreen 0;wait 200; vid_restart; set switch vstr fullscreen"

script seems to work :) thx

---

### Post by endy on 2005-09-21
You could always do something *better* than ET minimiser ;)

Here is a guide I made that runs ET on a new desktop so you can switch between ET and your desktop easily: 

[HOW TO: Run games on a new X server](http://ubuntuforums.org/showthread.php?t=51486)

This makes sure that you don't get kicked from a server becasue you have "r_fullscreen 0" set which I know ETPro / Punkbuster checks :)

---

### Post by shawn on 2005-09-21
Endy's HOWTO is totally the best thing for this. I use it for all my games Wesnoth, Doom 3, ET. I tried Xgame which lots of people reccomend but I prefer endy's way. If you use endy's HOWTO then you will have to turn off the screensaver on your desktop as it still gets activated because there is no activity on that X server, I don't think that was mentioned in the thread.

---

### Post by krak on 2005-09-21
i have tried running new X but error came.
***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

waiting for X server to shut down

just the new X dont have my ati drivers ON how so what i have to do to read my xorg.conf ??

---

### Post by endy on 2005-09-22
Yeah, I should have said that some people have trouble with the ATI drivers :( All I can suggest (as not having an ATI card to test with) is to try again whenever the drivers are updated or seek help from other ATI users, until then I guess dontpanic's method is best :)

---

### Post by tuesday20102001 on 2008-06-24
> **endy said:**
> You could always do something *better* than ET minimiser ;)

Here is a guide I made that runs ET on a new desktop so you can switch between ET and your desktop easily: 

[HOW TO: Run games on a new X server](http://ubuntuforums.org/showthread.php?t=51486)

This makes sure that you don't get kicked from a server becasue you have "r_fullscreen 0" set which I know ETPro / Punkbuster checks :)

careful consideration:
I did read the script written on other post. Although this work around may work, it is a major security risk. reasons being listed: [http://www.xs4all.nl/~zweije/xauth-6.html](http://www.xs4all.nl/~zweije/xauth-6.html)

what potential attackers can do listed here: [http://judebert.com/progress/archives/158-Starting-a-Stealth-X-Server-Display.html](http://judebert.com/progress/archives/158-Starting-a-Stealth-X-Server-Display.html)

I like the ideal of the light weight execution of the games, but not worth the security risk for me.

Something to consider?

---

### Post by 1337 on 2008-06-25
It's called ETSwitch it's a minimizer written for Enemy Territory and other Quake based games. You can get binary deb package [here]("http://www.getdeb.net/app/ETSwitch"). No need for scripts or another X seession :P.

Regards

---

### Post by lillypop on 2008-06-28
I just downloaded and installed the et switch but i have no idea how to use it lol
I can't find and manual for it to tell me what key to press to minimize or even what comand to type .
Any help would be appriecated with xp the et min just works by pressing alt+z .

---

