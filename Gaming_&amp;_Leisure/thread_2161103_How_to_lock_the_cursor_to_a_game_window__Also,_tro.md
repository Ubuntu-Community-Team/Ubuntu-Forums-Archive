---
title: "How to lock the cursor to a game window?  Also, trouble with a fullscreen game."
date: 2013-07-09
forum: Gaming &amp; Leisure
---

### Post by snakeman21 on 2013-07-09
Hey all.  I'm having an issue with a game, and in using a temporary "workaround" (quotations because I use the term very loosely here), another issue arose.  

First issue is this.  I am playing SWAT4 on my Ubuntu 13.04 machine.  The game installed and runs seemingly perfectly under Wine.  This game is fullscreen only, there is no option for a windowed mode.  But when playing the game, the screen does that thing where it displays a low-res version of your Unity or Gnome panel (whichever your system uses) centered at the top of the game.  I use Cairo-Dock, so that also appears at the bottom every time I move the mouse down to far.  Changing windows version and graphics options from Wine did not solve this, nor did trying every resolution option in the game menu.  This is a minor annoyance and does not affect gameplay, because even when Cairo-Dock is activated, it cannot be clicked or otherwise interacted with.  But I found out what the culprit was:  When going into Wine configuration, I discovered that unticking "Allow the window manager to control the windows" fixed the problem and I got flawless fullscreen graphics.  However, after hours of googling and trying, I simply could not get the game to detect the keyboard with this option turned off.  I tried everything, to no avail.

Which leads me to my next issue:  The mouse.  I figured that I could tell Wine to emulate a virtual dekstop and get a windowed mode (sort of) that way.  However, SWAT4 is a first-person shooter, and moving the mouse too far in any direction makes the cursor leave the game window and stop controlling the game.  I cannot play it well when trying to turn to face an enemy results in the cursor leaving the window and not controlling the game anymore.  I tried googling a method to lock the cursor to a specific window, but could not find anything. 

Solving either one of these issues would be satisfactory, but I'd prefer the fist one.  Fullscreen gives the game a more "immersive" feel.

---

### Post by oldrocker99 on 2013-07-09
You could try installing KDE, which is not **quite** as fast as Openbox or LXDE for full-screen gaming, but which does have the option in Video Effects on the third tab to disable effects for full-screen windows, making it pretty speedy for full-screen gaming. Razor-qt is in the 13.04 Universe repos, and it's very lightweight, though still needs some work. XCFE might also work better; I like the XCFE mouse...

---

