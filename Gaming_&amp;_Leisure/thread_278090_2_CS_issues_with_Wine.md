---
title: "2 CS issues with Wine"
date: 2006-10-15
forum: Gaming &amp; Leisure
---

### Post by AJLChase on 2006-10-15
I did get steam installed using Wine, and also got my account updated to download CS. My issues that I'm running into are these. When I go to play Counter Strike....the main menu that lets me choose my games that I would like to play along with friends list and everything else, stays on my screen. Even while I am in game it's in my way. Now If i try to minimize it, it freezes my whole computer, and I have to reboot. Then when I go into my steam folder to start steam again, I get a steam-fatal error.Could not load module bin/vgui2....an help would be greatly apprecaited.

---

### Post by livinginx on 2006-10-31
For the games list being in your way, double click CS, then click the X in the game list window.  I had that a few times too.

I am having sound lag issues with my CS

---

### Post by electricshoes on 2006-10-31
>  I am having sound lag issues with my CS

Are you using OSS or Alsa for your wine audio ?

---

### Post by haxer on 2006-10-31
why use wine look at google for steam4linux then you will see my guide to set it up here on ubuntu forums :)

---

### Post by electricshoes on 2006-10-31
Hey cool.. Ive never seen that before. Thanks,.

---

### Post by haxer on 2006-10-31
Np mate ;)

---

### Post by livinginx on 2006-10-31
> **electricshoes said:**
> Are you using OSS or Alsa for your wine audio ?

I got it now.  Using OSS.  Didn't have audio configured in WINE.

However, my voice comm is really choppy.  Any ideas on that one?  I will check your steam4linux post sometime.

---

### Post by electricshoes on 2006-10-31
> **livinginx said:**
> However, my voice comm is really choppy.  Any ideas on that one?

Here are the settings that I use, I cant find the how-to i used but only with these settings I get CS:S to run perfectly no matter what resolution or effects I have on.

```
$ winecfg
```Applications - Windows Version - Windows 98
Graphics - Everything is checked in here.
-----------emulate a virtual desktop - 1024x768 [B](the window       steam would run in.)
[/B]-----------vertex shader support: Hardware
Audio - OSS

 The script I have to run Steam
```
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen -heapsize 512000
```Then what I do is right click on CounterStrike go to properties and under launch options put 

```
-fullscreen
```This will get rid of the border on the bottom of the cs window when the game runs.

In the game you can change the resolution to whatever you want. For me if I change the resolution and apply it my mouse gets kinda wierd. So i exit and relaunch it and it will save your settings.

Thats what I do. If I run different winecfg settings the game will run but i will get choppy times like the map is trying to load. This might be happening when your voice is wonky.

---

### Post by livinginx on 2006-10-31
Yeah, I pretty much have those same settings, but I don't emulate a virtual desktop.

Some reason, just really choppy voice comm.

Might do some research tonight and find out if there is a better OSS driver for use with an nforce2 chipset.

---

### Post by electricshoes on 2006-11-01
hmm wierd. hope you get it figured out, sorry I couldnt be of more help.

---

