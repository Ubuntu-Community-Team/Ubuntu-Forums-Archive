---
title: "Window Edges"
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by Harkainos on 2007-04-17
So I have Wine installed. I patched the nvidia_glx drivers and ran UT2004 (I know there is a Linux version, but I am 10 hours old to Linux). Everything seems to work flawlessly, except when my 'mouse' would logically hit the edge of the screen... i can't turn, or look up and down.

Any suggestions? If you are a seasoned Linux Gamer, maybe you could gimme some wine pointers as well. Maybe the best settings or what not. 

Also, I am running a duel boot, which incidentally windows xp pro isn't loading (not the point), could i run wine from those already installed apps?

---

### Post by buttons on 2007-04-17
> **Harkainos said:**
> So I have Wine installed. I patched the nvidia_glx drivers and ran UT2004 (I know there is a Linux version, but I am 10 hours old to Linux). Everything seems to work flawlessly, except when my 'mouse' would logically hit the edge of the screen... i can't turn, or look up and down.

Any suggestions? If you are a seasoned Linux Gamer, maybe you could gimme some wine pointers as well. Maybe the best settings or what not. 

Also, I am running a duel boot, which incidentally windows xp pro isn't loading (not the point), could i run wine from those already installed apps?

I believe the answer to your problem lies in DX_GRAB being set to no.  Essentially what this does is allow directX games to cage your mouse within the window.  When playing fullscreen, this is a Good Thing.

The easiest way to set this is to fire up a terminal, and run:
```
winecfg
```
Then tab over to Graphics, and the first checkbox is "Allow DirectX apps to stop the mouse from leaving the window."  Check it.  Making sure "Allow the window manager to control the windows" is also checked is a good idea.

Hit okay and try it again.

Though as you mentioned, the official client is much better.  Instructions for installation can be found pretty easily by searching the boards, depending on which version you're trying to install from.

---

### Post by Harkainos on 2007-04-17
Thanks. I will certainly try that.

---

### Post by Harkainos on 2007-04-17
I tried this and it still stops. It is as though there is a background mouse and when it hits the edge of the screen, i cannot turn anymore

---

### Post by Harkainos on 2007-04-17
I just got WoW to run. YAY.... now

I cannot get the game to go higher than 800*600. And the highest resolution Ubuntu has (that i can see) is 1152*864.

First, how do i get higher resolutions in Ubuntu?

Secondly, with WoW Resolution being 800*600 i can actually 'push' passed the game and see the desktop on bottom/right side. What is causing this?

---

### Post by Harkainos on 2007-04-20
I got Ubuntu to get 1440*900 Screen Resoultion. YaY

I edited the config.wtf file in WoW to set it at 1440*900. I think the x11 feature was causing problem and 'resetting' when i changed resolution in game.... so I bypassed that and just editted the default.


I am on the other hand still having trouble with UT2004. It is like the desktop mouse is still active and when that mouse hits the edge of the desktop (in the background) I cant turn any farther.

---

### Post by AndrewRiedi on 2007-04-20
Open a terminal and type: **wine --version**

What does it give?

---

### Post by Harkainos on 2007-04-24
9.3 - something


It is still happening. Not sure why.

---

