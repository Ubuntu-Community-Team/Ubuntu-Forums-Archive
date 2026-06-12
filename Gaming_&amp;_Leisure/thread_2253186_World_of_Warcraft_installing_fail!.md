---
title: "World of Warcraft installing fail!"
date: 2014-11-17
forum: Gaming &amp; Leisure
---

### Post by Austen_ on 2014-11-17
Hey i'm new to linux and all so please if any answers seem to technical for beginners please dumb it down for me! lol  But anyways I've been trying to install World of Warcraft on my pc through linux, now I tried doing it through wine, manually doing it with terminal and also using "playonlinux."  Sadly all these did not work and had the same issue which might be a simple fix but I couldn't figure out how to do it.  After I install everything and log into my account.  I try to start up the Battle.net application, it loads but then sends me a error box, on top says Battle and in the description it says "this application failed to start because it could not find or load the Qt platform plugin "windows"."  It suggested reinstallling but I have a solid 3 times on each way I attempted to get this to install.  I downloaded this application that I thought might help but get lost in called Qt Creator.  Links or a solid guide on how to help get this issue resolved would make my Thanksgiving! haha  

- Love, Austen

---

### Post by SirMoo on 2014-11-19
You will need to set wine's windows version to XP for battle.net to work. Only way to get around the QT issue currently. Type winecfg into the terminal and go from there.

Next I encourage you to set the following overrides. (If you need instructions on that let me know... I don't know how much you want it dumbed down). 

**DBGHELP** disabled
**battle.net** native, builtin

After that run battle.net from the terminal 

*wine 'path-to-wine' --nohttpauth*

The *--nohttpauth *was required for me to be able to download, otherwise things just crash. If it looks like it crashes or locks up, just check the terminal and it will have the progress listed every 10 seconds or so. 

App DB has some discussion on it. [https://appdb.winehq.org/objectManager.php?sClass=version&iId=28855](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28855)

Personally, I can not get it to run with 1.7 wine and have to downgrade to 1.6.

---

### Post by mchunt3 on 2014-11-19
I'm an utter linux noob as well. I have WoW running on Wine 1.7.31 without Playonlinux following the instructions at [http://geebzor.com/tech/linux/wow-ubuntu-14-04-trusty/]("http://geebzor.com/tech/linux/wow-ubuntu-14-04-trusty/")

There are some caveats. 
1) There is a weird buzzing in the sound. I haven't been able to sort that out yet.
2) I can't get the desktop icons to do anything useful, or it feels like they aren't doing anything useful. Either way I'm launching both battle.net and wow-64.exe from the terminal. To make it easier I wrote a couple of bash scripts.
Open gedit, and create a file called wow.sh

#!/bin/bash
wine ./wine/drive_c/"Program Files (x86)"/"World of Warcraft"/Wow-64.exe <----Check the path. I'm doing this from memory while at work. Also, choose Wow.exe if you don't want to use the 64-bit client.

Use the same technique to create a separate script for battlenet. I haven't been able to download the updates from Blizzard unless I launch the battlenet app from the terminal. I haven't a clue why.

I also can't alt+tab from WoW without crashing the client while in fullscreen mode. 

Other than that I've been able to play without much trouble. I think the key is to make sure Wine is up to date, as well as your video drivers. I have an ATI video card which comes with it's own headaches. And that part on Geebzor's page about setting the graphics to OpenGL? Do it. Just for fun I switched OpenGl back to D3D9 and my frame rates dropped from 60fps to 4fps.

Good luck!

---

### Post by Austen_ on 2014-11-19
Thank you guys!  I actually had wine 1.5(something else) and I did a update on wine then re loaded the application to give it another go.  Really appreciate the answers, loving the communty :D

---

