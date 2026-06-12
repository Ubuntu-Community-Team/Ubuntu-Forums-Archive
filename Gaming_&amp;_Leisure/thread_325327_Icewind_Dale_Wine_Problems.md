---
title: "Icewind Dale Wine Problems"
date: 2006-12-25
forum: Gaming &amp; Leisure
---

### Post by ShanghaiTeej on 2006-12-25
I installed wine and Icewind Dale without a hitch, but when I tried to start Icewind Dale, I get an error that says:  "An Assertion failed in ChVideo.cpp at line number 5683 Programmer says: No valid video modes supported."  

I remember I declined to install Icewind Dale's directx drivers, should I go back and accept that driver?  If anyone can help me, you are my hero.

---

### Post by foolsh on 2006-12-26
which version of icewind dale 1? 2? 3? is there a 3rd one? and which version of wine are you using. I've got some free time and a couple of versions of IWD i'll take a look and see what comes up.

---

### Post by foolsh on 2006-12-26
well I installed IWD1 Btw wine ver 0.9.28 was released the other day might want to update to that one i don't have to same problem as you. installed just fine but freeze during the opening video. this can be worked around by pressing escape shortly after the videos start.
it takes a few tries but I did get it to run

 no you shouldn't have to install the directx that came with IWD wine implements its own dirextx api 


try running winecfg and setting wine to emulate a desktop in a window i have mine set to 800x600
make sure your cdrom is selected on the drives tab
im not sure if IWD uses midi for music playback but i have timidity installed

run the IWD config program and set the color bit to your desktop color bit i.e. 16 24 32
make sure the opengl option is NOT selected

its seems playable i only walked around i bit and closed the game

here is a screen shot
[IMG]http://foolsh.home.insightbb.com/snapshot3.jpg[/IMG]

---

### Post by ShanghaiTeej on 2006-12-28
thanks for the help, but I have fiddled with winecfg (turning settings on and off) and Icewind dale configuration and can't get it to work.  I run into the same prompt every time.

#()*)($#*)(# UPDATE*&#(*$(#

Changing my desktop window size in winecfg was the answer.  Thanks for your help, I got it working now!!!!  Foolsh, you are kick *** in my book.

---

