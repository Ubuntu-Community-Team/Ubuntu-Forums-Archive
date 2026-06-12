---
title: "Fallout 2 in Wine... no hardware acceleration?"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by skelooth on 2005-12-25
Hi. afaik i have wine set up properly. It runs photoshop and all that jazz no problem.

The problem with gaming is that it changes the resolution of the desktop and just puts the game on my desktop like a normal window... it never actually gives the game fullscreen control. I have fallout2 installed but everytime the screen fades it goes MEGA slow....

how can I give wine 'real' full screen control + hardware acceleration?

---

### Post by Perfect Storm on 2005-12-25
tried with -opengl and see if it helps?

Like

wine "/blah/blah/blah/bleh/fallout2.exe" -opengl

---

### Post by Perfect Storm on 2005-12-25
Or you could checkout this: [http://happypenguin.org/show?IanOut](http://happypenguin.org/show?IanOut)

---

### Post by skelooth on 2005-12-25
no go with running with -opengl or --opengl (I don't think ogl was really used back then???)

and FIFE/IanOut doesn't seem to have anything available to download at the moment.... :\

---

### Post by Perfect Storm on 2005-12-25
Sorry can't help you further :/ I don't own the game....

---

### Post by skelooth on 2005-12-25
Okay, well i figured out how to give wine full screen control.... 

# X :1.0

then in another terminal

# export DISPLAY=:1.0
# xterm

then you can go between the displays with ctrl+alt+F7||F8

But when i try to start fallout this way it says"unable to find fonts" and ends.

I was able to start warcraft 3 this way in ogl mode, but the performance is TERRIBLE. I have ~900mb of ram and a geforce fx 5200 ultra and wc3 was not playable...

---

