---
title: "Compiz-Fusion exists but doesn't do zip"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by tadada on 2007-08-10
Ok I installed fusion and everything went without a hitch, Uninstalled desktop-effects then installed it. I then used "compiz --replace" in the run command. Nothing happened. So I restarted and reran the command. still nothin. I can change compiz's settings using System --> Prefrences --> CompizConfig Settings Manager. I don't have Emerald installed just Compiz-F. Everything is absolutley fine except for that compiz is doing zip and nadda. 

I have a Pentium 4 (the older 2.4 ghz) 512 mb of ram 1 gig swap and an ATI 1300X Pro GFX card using the FGLRX driver

can anyone help me with this problem

---

### Post by tadada on 2007-08-10
I looked around a bit and I have seen stuff about AIXGL and XGL do I need either of these and if so where can I find a install tutorial?

---

### Post by janbockaert on 2007-08-11
Yes, you have to install xgl, the binary ati-driver does not support aiglx. After you installed xgl, you will have to create a script, and a session, to start the xgl driver (google for ati+xgl+feisty). or you can use the opensource ati-driver (also google for how to change that - i'm a nvidia user). The OS ati driver should be working with aiglx. (aiglx is part of x.org, no need to install aiglx).

---

### Post by petit.padavoine on 2007-08-11
[http://www.compiz.org/ATI](http://www.compiz.org/ATI), if it helps. I'm also an nVidia user so can't help much :D

---

### Post by tadada on 2007-08-11
Thanks I got it working :)

---

