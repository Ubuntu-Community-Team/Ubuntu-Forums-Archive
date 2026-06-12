---
title: "No FrontEnd for Mathematica 7.0 on dual screen Ubuntu"
date: 2009-01-31
forum: Education &amp; Science
---

### Post by FullArgon on 2009-01-31
Hello guys:

Does anybody know how to make that the Mathematica 7.0 FrontEnd shows up when you have dual screen?

I'm using a NVIDIA GeForce 8400 GS with a nvidia-glx-new-envy driver. If I set up only one screen to work, Mathematica starts well and the FrontEnd shows up. If I configure the TwinView dual screen option, it still works fine. But when I setup the Separate X screens, Mathematica is not able to pop up the GUI. I think the problem has to do with the variable DISPLAY. So far I haven't seen any option in Mathematica that allows me to pick the screen I want to use :(

If anybody has experienced something similar and know how to fix the problem, please advise.

---

### Post by kaspar_silas on 2009-02-05
I am also running Mathematica 7.0 but I don't have any problems. Are you running the linux version or the windows version through wine?

Also try mathematica -defaultvisual

---

### Post by The_3cHeLoN on 2009-03-22
I want to confirm this problem, I am using mathematica on zenwalk, but there I have the same issue.

---

### Post by sosostris on 2009-04-05
Can confirm this problem with Mathematica 7 and nvidia 8600GT separate x-screen setup. The process seems to hang at futex_wait in the process manager.

---

### Post by Avoozl on 2009-05-18
I can also confirm with Mathematica 7 running on dual screen (separate x) in Intrepid 32 bit, NVidia 7800GS.  However I have a strange workaround.  I have an old script I ran with Mathematica 5 a while back:

```

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1

mathematica

```

This code produces a "segmentation fault" when running from the command line, presumably from the first command (I don't remember what it's supposed to do), but after that Mathematica launches with the GUI and appears to run fine.

---

### Post by josemanuel on 2010-06-16
Hello, I confirm  the problem and the short-cut. I have ubuntu 10.04 and Mathematica 7.0.  Graphics card is  a NVIDIA GeForce 8400M GS .  As soon as I changed to separate screen mode, no frontend at all.  The provided script is a temporary workaround for me. I hope Ubuntu developers fix that bug in the future. Thanks for your help

                                      Jose Manuel

---

