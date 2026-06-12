---
title: "Help with video framerate"
date: 2006-04-12
forum: Desktop Environments
---

### Post by braveerudite on 2006-04-12
Hi all 

I am trying to watch an approx. 178 MB _avi_ episode (from Hard Disk) of "Ghost in the Shell" but I'm getting very poor framerate.  The only application I have manage to succesfully open these files with is with Xine-UI.  I get error messages with Kaffeine and Totem.

Audio is _no_ problem at all but my fps is too low.  Not only this but everything I use in Ubuntu seems visually  laggy. 

I have increased my Mobo's build in VGA Share Ram up to 64MB but the problem is still there.
Resolution I'm using is 1280x1024, I also drecreased the resolution to 1024x768 but still made no difference.

What am I doing wrong?  ](*,)

---

### Post by dcstar on 2006-04-13
[QUOTE=braveerudite]Hi all

I am trying to watch an approx. 178 MB _avi_ episode (from Hard Disk) of "Ghost in the Shell" but I'm getting very poor framerate.  The only application I have manage to successfully open these files with is with Xine-UI.  I get error messages with Kaffeine and Totem.

Audio is _no_ problem at all but my fps is too low.  Not only this but everything I use in Ubuntu seems visually  laggy.

I have increased my Mobo's build in VGA Share Ram up to 64MB but the problem is still there.
Resolution I'm using is 1280x1024, I also decreased the resolution to 1024x768 but still made no difference.

What am I doing wrong?  ](*,)[/QUOTE]
Run glxinfo and see if **Direct Rendering** (which is video hardware acceleration) is enabled, if not do a forum search for your video hardware for instructions on how to get it working.

---

### Post by braveerudite on 2006-04-13
[QUOTE=dcstar]Run glxinfo and see if **Direct Rendering** (which is video hardware acceleration) is enabled, if not do a forum search for your video hardware for instructions on how to get it working.[/QUOTE]
______________________________________________________________________-

jok3r@ubuntu:~$ sudo glxinfo
Password:
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
______________________________________________________________________

I'm using Dapper Drake Flight 6.04 (64 Bit version)   but I had same problem with 5.10 32 Bit version.

I get a very choppy drop of framerate only when I'm using full screen.

---

