---
title: "Xvfb display problem"
date: 2008-12-16
forum: General Help
---

### Post by pasayten on 2008-12-16
I am running a older (2005) vintage weather climate image generation and display program called "pave"  (or "pave_exe") from the cmas modeling org.  Running intereactively in DISPLAY :0.0, as default it runs fine.  I would like to run it in batch and use Xvfb to use a DISPLAY :1 so it will not display on my screen while running.   It is set up this way on many of our other servers around here and it runs fine that way.

When I use:  
Xvfb :1 -screen 1 1600x1200x16 -fbdir /tmp/Xvfb_1 &
export DISPLAY=:1

and then run pave, I get:

Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :1

I have tried "xhost +" and that did not make any difference.

I am running ubuntu 8.04LT

Anybody have any ideas on how to track the problem down?

Thanks in advance!

Ray (pasayten)

---

### Post by pasayten on 2008-12-17
I came across the xvfb-run command and tagging the pave application on the end of it runs fine...

I guess xvfb-run takes care of xauth stuff...  whatever...  all is well with the xvfb-run command.

---

