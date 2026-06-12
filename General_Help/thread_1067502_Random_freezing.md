---
title: "Random freezing"
date: 2009-02-11
forum: General Help
---

### Post by kerryhall on 2009-02-11
Ugh, this is such a frustrating problem. Here goes. Gnome seems to freeze randomly. I can still move the mouse, but clicking on things has no effect. This can last for up to several minutes, and happens seemingly at random. I can still ctrl alt f1 to a terminal, and run top to see what is hogging all the cpu cycles. It's always nothing. Usually doing ctrl alt f1 then ctrl alt f7 seems to unfreeze gnome, but not sure about that. Please help, this is driving me nuts! (Perhaps this is a hardware problem?) Intrepid Ibex.

---

### Post by HermanAB on 2009-02-11
This can be due to a bug in a device driver.  Try divide and conquer to localize the problem.  For example, power down and unplug the CD drive, then see if it still happens.

Cheers,

Herman

---

### Post by Bonsanto on 2009-02-14
Same problem here :D

---

### Post by kerryhall on 2009-02-14
Is there a way I can try and localize the problem without removing specific hardware?

Is there a way I can see any sort of error output that the device drivers are giving me?

---

### Post by kerryhall on 2009-02-18
Bump.

---

### Post by Crafty Kisses on 2009-02-18
Try checking your kernel logs and see if you see anything out of the ordinary:
```
sudo nano /var/log/kern.log
```

---

### Post by kerryhall on 2009-02-18
Thanks! I'll give that a try and see what I get.

---

### Post by kerryhall on 2009-02-25
I see nothing that looks out of the ordinary. Would it say something like "driver error" ?

---

