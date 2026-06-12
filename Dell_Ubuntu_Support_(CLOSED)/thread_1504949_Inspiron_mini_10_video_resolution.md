---
title: "Inspiron mini 10 video resolution"
date: 2010-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pookito on 2010-06-08
Short version.  I call dell to buy a mini 10 with Gnu/Linux and I end up with a window 7 edition.  Which I totally hate, So I decided to put Lucid in it.  It worked perfectly but the video card was not giving me the right resolution.  So I found this: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#fnref-decc23b80ed43a68975ee3dc13ecb82a311f9ba1](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#fnref-decc23b80ed43a68975ee3dc13ecb82a311f9ba1)

Which I followed step by step, but for some reason now X does not want to start completely.  So I when to a shell and looking on the net I realized that I needed the proper module which I included when I logged in the shell: modprobe psb when I start x at the shell level it has beautiful graphic.  Now, when I start the kernell, x still does not want to start. 

Please, somebody help me.

:(

---

