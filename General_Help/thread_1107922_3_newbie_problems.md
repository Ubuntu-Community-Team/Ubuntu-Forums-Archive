---
title: "3 newbie problems"
date: 2009-03-27
forum: General Help
---

### Post by bambuin on 2009-03-27
hi i just got ubuntu 8.10 4 days ago and i have 3 little problems

1. when i play any video (avi, mpeg, mp4...)the image is flashing all the time, so i can't watch anything without a headache

2. the firefox window is too big that i can't see the panel anymore, or the minimize-maximize-close buttons of the same window. i can only quit from the file.

3. the internet connection is wireless and is automatically when the ubuntu starts. If it doesn't start automatically, is there a button who says "connect"?

thnx a lot guys

---

### Post by FnMag on 2009-03-27
upper right hand corner you should have a signal strength meter. Click it to allow connection to any available wireless networks found? As far as automagically doing that, I am brand new and don't know yet..

---

### Post by Onesimus on 2009-03-27
> **bambuin said:**
> hi i just got ubuntu 8.10 4 days ago and i have 3 little problems

1. when i play any video (avi, mpeg, mp4...)the image is flashing all the time, so i can't watch anything without a headache

2. the firefox window is too big that i can't see the panel anymore, or the minimize-maximize-close buttons of the same window. i can only quit from the file.

3. the internet connection is wireless and is automatically when the ubuntu starts. If it doesn't start automatically, is there a button who says "connect"?

thnx a lot guys

Solution to No. 1
See this link [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Solution to No. 2
Hold down the Alt key and the left mouse button and move the window.

Solution to No. 3
Right click on the wireless widget on top panel, and de-select the Networking, then re-select it.  It should then connect.

Hope this helps

---

### Post by elliotn on 2009-03-27
For 1. I think u need the gstreamer ugly plugins,


2. Am not sure but check your screen resolution.

---

### Post by bambuin on 2009-03-27
1. i already have the the gstreamer ugly plugins

2.hmmm... alt and left clic doesn t do anything. This problem, i have it only with firefox so i don't think it will be a problem of screen resolution...
:(

---

### Post by bryncoles on 2009-03-27
your firefox issue sounds like its starting in full screen mode. if this is the case, try pressing f11 (maybe twice) this should move it back to a sensible size.

***edit:***

follow this guide

[http://midnight-freak.blogspot.com/2008/08/profiles-in-ubuntu-firefox.html](http://midnight-freak.blogspot.com/2008/08/profiles-in-ubuntu-firefox.html)

to creating a new firefox profile. if im right about firefox starting in full-screen mode by default, this should solve the problem.

---

### Post by bambuin on 2009-03-27
al right!!!
the video problem resolved by gnommplayer and bryncoles u r right about firefox
i ll try now to resolve it with the solution in your link.

thnx a lot

---

### Post by gorucan on 2009-03-27
> 3. the internet connection is wireless and is automatically when the ubuntu starts. If it doesn't start automatically, is there a button who says "connect"?

right click on connection tray in top right corner.

---

### Post by PrinceArithon on 2009-03-27
> **bryncoles said:**
> your firefox issue sounds like its starting in full screen mode. if this is the case, try pressing f11 (maybe twice) this should move it back to a sensible size.

***edit:***

follow this guide

[http://midnight-freak.blogspot.com/2008/08/profiles-in-ubuntu-firefox.html](http://midnight-freak.blogspot.com/2008/08/profiles-in-ubuntu-firefox.html)

to creating a new firefox profile. if im right about firefox starting in full-screen mode by default, this should solve the problem.

You beat me with the F11 key advice.

It seems the reason why Firefox does this is because of Compiz.  If you turn it off it will fix the problem, but it sucks if you like Compiz like I do.

The only other thing you can try doing is after you done your temporary fix with F11, and everything is in order, Unmaximize the window and grab the browser window from the top and resize it manually to where it's smaller.  It doesn't matter how small you resize it just make sure you make it noticeably smaller.  Then after that maximize the window again.  You may have to resize it like this a few times before it finally fixes...it's what I had to do..

---

### Post by perpetualcacophany on 2009-03-27
> **PrinceArithon said:**
> 
It seems the reason why Firefox does this is because of Compiz.  If you turn it off it will fix the problem, but it sucks if you like Compiz like I do.

You don't have to completely disable compiz.

Get CCSM (sudo apt-get install compizconfig-settings-manager)

Open it and go to Workarounds

unselect "Legacy Fullscreen Support"

---

### Post by PrinceArithon on 2009-03-27
Oh totally awesome, I could never find a better fix than the one that I did to fix it which I still have to do once in a while by resizing the browser lol.

I'll try it out now.

Edit:

OK I had a bit of a hard time finding Workarounds.  But it's in the Utility section, and you have to click on it to open it up.  I just figured I'd throw that out there in case anyone had some problems.

---

### Post by bambuin on 2009-03-27
yeah! finally to resolve it, i did what prince did. Key f11 helped me.
perpetual, i tryed to install ccsm, but it sorted some errors...

---

