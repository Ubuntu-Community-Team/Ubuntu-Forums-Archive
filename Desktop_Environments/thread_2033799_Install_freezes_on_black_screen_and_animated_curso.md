---
title: "Install freezes on black screen and animated cursor"
date: 2012-07-26
forum: Desktop Environments
---

### Post by LHammonds on 2012-07-26
I have a small army of IBM NetVista PCs (1.8GHz), 384-512MB RAM, 10-40 GB drives.  A fresh copy of Windows XP is simply too slow for these old work dogs so I would like to install a snappier OS.  I tried Puppy Linux 5.2.8 but it seemed too terse to hand over to casual PC users that just want to surf the net and watch DVDs.  The most lightweight version of Ubuntu I could find was Lubuntu and I'd like to get that working if at all possible since it seems to be a good mix of performance and user-friendliness.

I think [this bug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/909179) is affecting my installation on these PCs.  However, I do not understand how one can "jump to a terminal" screen and delete files when you are in the process of installing bare-metal to a new PC.

I have also tried turning off various F6 options such as **noapic** and **nolapic** but cannot get past the "copying files" part shortly after it asks for your Name, PC Name, ID and password.  It shows a couple of info screens and the last one mentions the LXDE desktop.  The screen goes black and the cursor shows a "thinking" animation.  The Numlock can still be toggled so the PC is not completely locked up but it does not respond to CTRL+C or CTRL+ALT+DEL either.  When it reaches this point, I have to pull the power.

The CD image that was downloaded was verified error free and the burned CD-ROM was also verified that it was made correctly and the disc was closed to prevent further writing.  I have also tested the hard drive, RAM and video card hardware and everything checks out OK.  I even installed Windows XP and got it fully patched just to make sure the system was stable (that took a couple of days!)

I'm stuck and out of ideas.

LHammonds

---

### Post by 2F4U on 2012-07-27
You should be able to get to a virtual console (terminal) by pressing, for example, Ctrl-Alt-F1 at the same time.

---

### Post by LHammonds on 2012-07-28
> **2F4U said:**
> You should be able to get to a virtual console (terminal) by pressing, for example, Ctrl-Alt-F1 at the same time.
That did the trick. Thanks for your help.  I had tried Ctrl+Alt+T but that apparently only works after you are in a fully installed desktop. But unlike the bug report instructions, the installation has to be started before a terminal can be accessed.

I was able to issue the command to delete the file but I'm now "stuck" at the terminal.  Typing "exit" only brings me back to the terminal again.  I have no clue what command I need to issue to continue/resume the installation.

Anyone know what to type to resume the installation?

---

### Post by LHammonds on 2012-08-04
I have tried to find the command that will resume the install but I cannot find it.

Does anyone know what to type at the terminal to resume the graphical installer?

[COLOR=Red]**EDIT**: Solution is to press **CTRL+ALT+F7**[/COLOR]

---

