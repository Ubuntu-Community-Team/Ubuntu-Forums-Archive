---
title: "Ubuntu and Day of Defeat Source"
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by littlespy on 2006-02-22
I'm not sure why but for some reason day of defeat source isn't working right for me.  Everything loads up alright and I connect to a server but it hangs at 'Sending Client Info'  There are no errors in cedega it just hangs there, I let go for about an hour.  Eventually cedega crashes, and I can even kill the x server with control + alt + backspace.  If anyone can help me, I'm not really sure what  logs or anything you would like to see but I can ofcourse send you them.

This same problem happened on my first AMD64 Ubuntu install, and now on a fresh x86 install.

---

### Post by littlespy on 2006-02-22
for anyone else that might come across this problem, I started hl2.exe with the params -heapsize 512000 and -dxlevel 70 and dod:s booted right into game

---

### Post by BathroomNinja on 2006-02-24
I've had simular problems with CS Source (same engine).  I was testing things out in XP and everything would work fine for a few days, and then suddenly, they stopped working in XP as well.  I also have an AMD 64.  In fact, after various seraches, I found that this problem seems to be related to the AMD 64 and Nvidia combo.  usually, some combo of the following seems to fix the issue in wine, cedega and in windows:

-dxlevel 70       (force DirectX 7)
-32bit             (force 32bit mode)

turning the audio to 2 speakers
using a windowed game instead of fullscreen
copying all files from the bin folder into the source folder.  (so like copying all files in the \steam\username\cssource\bin  folder into \steam\username\scsource)

---

### Post by snowblind on 2006-05-23
Hi guys, i could do with an update on this just to clarify it. shoudl i be runnign this as wine steam.exe - dxlevel 70.

Or is there a way to run steam hl2.exe -dxlevel 70

Apologise for old thread revival.

---

### Post by d3v1150m471c on 2009-12-18
Get virtualbox in your synaptic package manager and run windows xp. install day of defeat onto the virtualbox run windows xp and you're good to go. I use it on mine and it works perfect. If you don't know which version of virtualbox to install go to [www.virtualbox.org]("http://www.virtualbox.org"). They have the ubuntu packages there, to include .deb. BTW day of defeat and steam take of a good bit of space so i strongly suggest you make windows xp's harddrive space a minimum of 15gb.

 If you have any questions with getting virtualbox up and running properly feel free to add a question to the thread or email me at [email]tempestas_lingua@yahoo.com[/email]

---

