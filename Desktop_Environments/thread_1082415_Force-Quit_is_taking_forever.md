---
title: "Force-Quit is taking forever"
date: 2009-02-27
forum: Desktop Environments
---

### Post by asuastrophysics on 2009-02-27
Can someone please help me figure out why system monitor is taking 20 minutes to start? Linux is *supposed* to isolate one program from another, so if one freezes/takes up too much memory, the whole OS doesnt crash. I am currently running VMWare-Player, and I dedicated 420 MB of RAM to this machine.

Current System Specs: 
AMD Athlon 3800+ 64 bit Single-Core
Hard Disk: 160GB, 20GB free
RAM: 1GB (I know it's not a lot, but ubuntu should run fine with 680MB available)
Graphics: ATI Radeon 2400 HD Pro 256MB

Current Running Programs: Cairo-dock, VMware Player, Rhythmbox, Firefox, and File Browser. 
(I can barely move the mouse, so I cant get a complete list of running processes)
VMWare is showing windowsxp pro sp1, and it is at idle, showing the desktop. 
Everything is grayed out and frozen. Is there some quick method for getting the system monitor up? (EG, Windows has CTRL+ALT+DELETE, which NEVER takes 30 minutes to appear)

---

### Post by jwbrase on 2009-02-27
I've seen Ctrl-Alt-Del take a long time on Windows. I've even the system freeze up so hard that Ctrl-Alt-Del didn't even work.

In any case: As soon as you boot up and have all of your programs except VMware running, go into System Monitor and see how much memory is being used. If it's more than 680 megs, you're using too much in VMware.

I know that my own computer will often show from the high 400's to the high 600's used. You may well not have enough memory for everything you're trying to run.

---

