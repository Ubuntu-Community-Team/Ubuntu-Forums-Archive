---
title: "Mesa on display :0 ATI on display :1"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by rmx on 2008-02-22
hello

I have installed fglrx driver from synaptics restricted drive.

```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


```

Then I installed xserver-xgl and enable compiz

Rebooted and notice:

```
rui@rmx:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

rui@rmx:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

```

The compiz effects are working, but 3D performance sucks.

Anyone can help me please

thanks 

RMX

---

### Post by noahsark1126 on 2008-02-22
Same problem.  Using fglrx 8.40.4 and an ati x1400.  Compiz and my 3d performance are pretty good, but it's still annoying, since it seems like some things don't understand the fglrx/xgl combo and don't work right.

I've searched through just about everything and found nothing, except, of course, switching to nvidia, which I am about ready to do.

---

### Post by lifewithryan on 2008-02-22
Is this causing a problem for you?

My machine does the same thing, but I actually prefer it.  I play my older GL games on display :0 and leave my compiz stuff on :1.

I have found that some programs don't like to be run under Compiz so well, so when i come across that, I usually bust out to the good ole command prompt and do:
```

export DISPLAY=:0

``` 

and run stuff that way.  

I think I had to do this to get Q3Arean to run smoothly for me.  (It's a really strange situation but I wanna say this whole issue is by design).

---

