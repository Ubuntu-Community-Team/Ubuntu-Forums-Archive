---
title: "Beryl halfway working; ATI and Xgl"
date: 2007-03-05
forum: Desktop Environments
---

### Post by amusser on 2007-03-05
I installed Beryl and I think it is only halfway working.  I installed version 0.2.0 svn because of the white screen problem.  When I select an Xgl session, I login and I get the gray screen with the black X and I never get the Beryl splash screen.  Then when the window manager loads, it looks like my Gnome session but I get the Emerald window decorations and the the windows are wavy when I move them and I get the window preview when I mouse over the taskbar, but I never get the cube and when I try to change settings in Beryl Manager nothing happens.  

I don't get any errors and everything seems to load fine.  I have an ATI Mobility Radeon 9600 Pro and I used these [instructions]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html").

Here are the relevant sections of my xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Extensions"
Option "Composite" "false"
EndSection


an output of ps shows beryl running

amy       5194     1  0 13:07 ?        00:00:00 beryl-manager
amy       5346  5194  0 13:07 ?        00:00:05 beryl-xgl


What could I have done wrong?  Am I missing something?

---

### Post by bimmerd00d on 2007-03-05
I think you forgot to enter 

sudo aticonfig --overlay-type=Xv  

after entering aticonfig --initial

---

### Post by amusser on 2007-03-05
> **bimmerd00d said:**
> I think you forgot to enter 

sudo aticonfig --overlay-type=Xv  

after entering aticonfig --initial

I never used the aticonfig command.  That wasn't mentioned in the instructions.  Do I only do that once?  Do I put it in a file?

---

### Post by amusser on 2007-03-05
I just tried the  **sudo aticonfig --overlay-type=Xv**  command and that did not fix it.

---

