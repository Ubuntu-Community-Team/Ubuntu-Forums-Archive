---
title: "Secret Maryo 0.99.5 + .deb"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by charlieg on 2007-04-03
Since it's only available in source form, I have built a .deb for the hi-res Super Mario clone [Secret Maryo]("http://www.secretmaryo.org/").

I used checkinstall.  No dependencies, no guarrantees, could eat your children etc.

Uncommon dependencies to install with Synaptic:
**cegui**

Get it here:
[http://www.filecrocodile.com/?d=C98FCF9B2](http://www.filecrocodile.com/?d=C98FCF9B2) (9megs, no music)
[http://www.filecrocodile.com/?d=B26A6BEE2](http://www.filecrocodile.com/?d=B26A6BEE2) (36megs)

If you don't have a 3D graphics card (32meg+) performance may suck.

---

### Post by Eddie Wilson on 2007-04-03
Tried but the link will not work.:confused: 
Eddie

---

### Post by charlieg on 2007-04-03
Yeah filecrocodile seems to have gone down.  Bah.

[edit] seems to be back again [/edit]

---

### Post by charlieg on 2007-04-03
Filecrocodile is back and I uploaded a version with music. :guitar:

---

### Post by gusjones on 2007-04-03
I can't resolve all the dependencies...

Resolved a few through synaptic, fell over trying to resolve "libCEGUIBase.so.1"
--it's not in synaptic and on a web browse I then tried to compile up something which created this package but this in turn failed... so I give up.

:confused:

---

### Post by charlieg on 2007-04-03
The one you want is **cegui**.

---

### Post by janfsd on 2007-04-03
I made a deb for amd64 users:

[http://rapidshare.com/files/24201167/smc_0.99.5-1_amd64.deb](http://rapidshare.com/files/24201167/smc_0.99.5-1_amd64.deb)

If u need libCEGUI then download this too:

[http://rapidshare.com/files/24201270/cegui_0.5.0-1_amd64.deb](http://rapidshare.com/files/24201270/cegui_0.5.0-1_amd64.deb)

Its the latest version of cegui, the one on Edgy is old so probably wont work.
Enjoy!!

---

### Post by sloggerkhan on 2007-04-04
I got it installed. It launches, and all. But then the snow looking stuff falls from the sky at like 1 frame per 3 seconds and the mouse bounces all over... am I missing something?

All my other games and such work OK.

---

### Post by sharperguy on 2007-04-04
What repo is cegui in because apt couldn't find it :(

---

### Post by charlieg on 2007-04-04
**sloggerkhan:** what gfx card?

**sharperguy:** do you have the community supported stuff in your sources.list?

```
deb http://gb.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
```

---

### Post by sloggerkhan on 2007-04-04
ati x700 open driver. Works fine with open arena and nexuiz and various other 3-D games.

---

### Post by charlieg on 2007-04-11
Got no idea, sorry bro.  Try the secret maryo forums on [www.secretmaryo.org](www.secretmaryo.org)?

---

### Post by Josey on 2007-04-11
I got it working with your .deb 
Thanks again.  :)

---

### Post by charlieg on 2007-04-16
You are welcome. :D

---

