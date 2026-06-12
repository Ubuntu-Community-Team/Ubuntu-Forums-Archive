---
title: "need some help with former windows applications..."
date: 2009-06-08
forum: General Help
---

### Post by thepiratefish on 2009-06-08
I just installed Ubuntu last night, and I have nooo idea what I'm doing...i thought it would be much easier. I was wondering if there's any way to get any of my former games to play. I can't even seem to get my emulated games to run on here...the emulator won't open.

Is there a program or something I can use to emulate windows on a small scale so that they'll play? or some sort of thing I can run these programs through?

---

### Post by Arup on 2009-06-08
Linux is not for gaming, having said that, there is WINE which lets you run Windows programs through Linux. Its in Ubuntu repositories and you can install from there, I however prefer installing it from their ppa site, its your choice.

---

### Post by synapsys on 2009-06-08
There are a few different ways to get your games working on Ubuntu. I would try using Wine for windows emulators and some games. PlayOnLinux for older commercial games. Cedega is a paid program that works with lots of newer commercial games. 

It's best to use native linux programs if you can. The only windows emulator I need to use is PJ64 (just plain don't like mupen64.) For the rest I use GFCE for nes, pcsx for psx, zsnes for snes, pcsx2 for ps2. All have native linux versions and work quite well. 

By the way to install wine open up a terminal from Applications >> Accessories >> Terminal and type:

```
sudo apt-get install wine
```Once installed it appears under Applications >> Wine.
To install programs simply download the windows executable and double click to open. If the default program is a movie player, right click the executable and use "Wine Windows Program Loader"

---

### Post by yoasif on 2009-06-08
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

also, what emulators are you using, and what problems are you having?

---

### Post by thepiratefish on 2009-06-08
right on. WINE is installing right now.

I use zsnes for super nintendo games, 1964 for n64 games, and nester for NES. are there better ones for Linux?

---

### Post by yoasif on 2009-06-08
zsnes is available for ubuntu, you can install it using the add/remove app. 

there is a megapost of emulator options here, you may be able to find more by searching the forum some more.

[http://ubuntuforums.org/showthread.php?t=612289](http://ubuntuforums.org/showthread.php?t=612289)

---

### Post by rcayea on 2009-06-08
Its true that Ubuntu Linux isn't the best OS for gaming, but I wouldn't never try to play them. 

I didn't see what games you are trying to play. Just be aware, some games work way easy with WINE. For example, this weird, addictive trucking game I like plays well with WINE. 

On the other hand, my favorite game of all time, Football Manager, I can never and still haven't been able to get it to work. 

Good luck, but just know it isn't easy as one, two, three...although some day it will be, I hope!

Randy

---

### Post by thepiratefish on 2009-06-09
Wine seemed to do the trick...but then again, doesn't it always? ;)

You know, I use a Lenovo Thinkpad R61, as supplied to all students by my college. I am amazed that all of the things I thought only worked with their Thinkpad software and drivers still work now that I have Ubuntu. 

Everything but a button at the top of my keyboard that would bring up a menu of Thinkpad options works. Is there some way to make it bring something else up? It doesn't do anything now when I press it, but I'm sure I can still find a use for it.

If necessary, I can take a pic of it. Do I have permission to post a photo on this forum?

---

