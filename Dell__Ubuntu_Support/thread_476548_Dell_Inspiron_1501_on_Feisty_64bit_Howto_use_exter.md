---
title: "Dell Inspiron 1501 on Feisty 64bit: Howto use external Monitor?"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by der_vegi on 2007-06-17
Hi!

I've got Feisty (AMD64) running on my Del Inspiron 1501 with an ATI Radeon Xpress 200M. Tomorrow I have to do a presentation and so I have to connect a projector to the monitor output of my notebook. Unfortunately, I don't have a monitor here to test it right now. But when I press the key Fn + CRT/LCD several times, nothing happens (I think it should switch to projector-only-mode at some time). What do I need to get the monitor plug working?

Thanks for the help!

---

### Post by der_vegi on 2007-06-17
Okay, kind of solved: It doesn't work, if I plug in the monitor when Ubuntu is already up. But if I plug it in before I switch the computer on, it works. Could be nicer, but well... ;)

---

### Post by neptho on 2007-06-17
What driver are you using?  If you've installed the fglrx driver, you can use aticonfig:

```
aticonfig --force-monitor=crt1,lcd
```

---

### Post by rabideau on 2007-07-12
I am having a similar (the same?) problem on my Dell e1505n.  Can anyone tell me what I need to set on my GeForce 7300 nVidia to make the Fn/F8 keys function?

Thanks!

---

