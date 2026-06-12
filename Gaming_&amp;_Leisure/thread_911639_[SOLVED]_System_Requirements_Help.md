---
title: "[SOLVED] System Requirements Help"
date: 2008-09-05
forum: Gaming &amp; Leisure
---

### Post by balahh on 2008-09-05
I was wondering if there was a program or command that would let me know what my system has. Like, for example, there is a site called [www.systemrequirementslab.com](www.systemrequirementslab.com) that tells you if your machine can run a certain game. I tried using this but Mozilla Firefox would not respond after reaching the download stage. Does anyone know of another program, command or even another website? Thanks :)

---

### Post by tamoneya on 2008-09-05
what stats are you looking for.  Here are some common ones:```
sudo lshw
cat /proc/cpuinfo
cat /proc/meminfo
```

---

### Post by jacksaff on 2008-09-05
You are trying to download and run a windows program that is going to query your system to see what it's hardware is. Linux is entirely different 'under the hood' than windows so this just isn't going to work even if you can get the program to run using wine.

Very few commercial games are written for linux. If you can run them at all it will be using something like wine which will mean the published system requirements won't be valid as wine works differently than windows. Sometimes the wine requirements are less than win as linux works better in a few areas though generally you'll need a slightly better system with linux/wine than you would with windows. Wine is not yet perfect.

It is not practical to write and maintain an accurate h/w requirements list for lin/wine. If your pc has the recommended (not the basic) h/w and the game you want is listed on wine's application database as working (gold status) then you should be good to go. Wine is good for dx8 and usually dx9 these days if the game lists them as requirements and your hardware is up to it.

---

### Post by kostkon on 2008-09-05
> **balahh said:**
> I was wondering if there was a program or command that would let me know what my system has. Like, for example, there is a site called [www.systemrequirementslab.com](www.systemrequirementslab.com) that tells you if your machine can run a certain game. I tried using this but Mozilla Firefox would not respond after reaching the download stage. Does anyone know of another program, command or even another website? Thanks :)
You can try [*lshw*]("http://ezix.org/project/wiki/HardwareLiSter") (*Hardware Lister*). Just install the *lshw-gtk* package from *Synaptic*.

---

### Post by balahh on 2008-09-08
Actually what I wanted to know were my hardware stats like for example what my video card is and my RAM, etc. Basically, I wanted to know if my system can meet the requirements listed at the back of the box of a video game. So assuming the game is listed in Wine, I wanted to know if there was a way for me to find out what my processor, memory, video card, etc. are so that I would know if I can play that game.

---

### Post by balahh on 2008-09-15
Bump :lolflag: I really want to know how to do this :) thanks

---

### Post by cisforcojo on 2008-09-15
```
sudo apt-get install sysinfo
```

This is the best I know of.

---

### Post by balahh on 2008-09-15
Sorry I'm new to this so I have no idea what to do after putting that in terminal :lolflag: it installed something and that was it. Now what? :confused: Sorry for the noob question :) Thanks :KS

---

### Post by Perfect Storm on 2008-09-15
You can find the app in Applications ---> System tool

---

### Post by cisforcojo on 2008-09-15
Yep, or just type 'sysinfo' in a terminal.

---

