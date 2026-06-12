---
title: "titlebar to drag wnindows?"
date: 2007-05-08
forum: Desktop Environments
---

### Post by guernicaaa on 2007-05-08
okay, here's my desktop
[http://www.fightoffyourpulse.com/help.jpg](http://www.fightoffyourpulse.com/help.jpg)
latest ubuntu, with beryl installed
i'm a linux noob and i'm sorry to  post here because you probably get so many of me a day, but here goes.

when I enable beryl, I lose the little titlebar that lets your drag and move windows around.  for instance, right now, without beryl, there's the titlebar that says "Ubuntu Forums - Post New Thread - Mozilla Firefox"
when I enable Beryl, that's gone and I can't move windows unless i right click in the taskbar thing and hit move.  anyone know what's up with that?

also, in that screenshot, I circled the taskbar at the bottom and put an arrow.  anyway I can stretch the bottom and top bars across both desktops?  im running two 19" Viewsonic LCD's, each at 1280X1024 75hz

---

### Post by WNDS1701 on 2007-05-08
Hey :-) 


I don't have used Beryl so far but to me it sounds like a setting that you would have to change in the Beryl settings.


I hope that this helps you in locating the problem.


Have fun and enjoy Ubuntu! I love it although I'm in for only 1 week :-)

---

### Post by guernicaaa on 2007-05-08
eh, I don't think it's just a simple setting.  I've racked through all those settings to try and find it.

---

### Post by guernicaaa on 2007-05-10
bump... nobody?

---

### Post by RaLX on 2007-05-21
The only fast solution is that you disable GL Desktop and Desktop Effects, I think there's something broken there :(

---

### Post by onbongos on 2007-05-23
you don't have a window manager running, for whatever reason

---

### Post by Maxwell7 on 2007-05-29
I can maybe help with this one. I've just solved a similar problem on my own pc. I'm running Feisty on a 4yr old Dell Inspiron with Nvidia Go5200 graphics card. 

I tried all of the things on the forums, but non helped for me. Finally after a lot of effort, I managed to get it running with all the cute titlebars and cool effects. It actually is quite simple. 

It does however include having to edit you xorg.conf file. Ok, enough chatter, here goes: 

First backup your xorg.conf file. Open up a terminal and type :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_b4_beryl
```
Next we'll add a line to that file. Open up a text editor
```
gksudo gedit /etc/X11/xorg.conf
```
then search for the section "Screen" There you have to add this > Option "AddARGBGLXVisuals" "True". Also make sure that the DefaultDepth is set to 24 !

This is how mine looks : 
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
```

Then restart your X-session by <Control> + <Alt> + <Backspace>. 

Now, once you start Beryl, things should be working fine, with titlebars and all :)
If however - like in my case - it doesn't work yet, you have to do one more little thing. 
Right click on the Beryl Manager icon in the top right bar, then select Advanced Beryl Options/Rendering Path/Copy 

After that, everything worked fine for me :-D 
Greetings & Good luck ! 

Maxwell

---

### Post by guernicaaa on 2007-05-29
ah, thanks a lot.  i already solved this a while ago doing the same thing you suggested that I found in another thread, just never reported back here.  thanks for the reply though, hopefully this will help some other people!

---

