---
title: "How to change video mode of freecraft?"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by Trosky on 2006-06-06
I have installed freecraft, but it doesn't start, I run through the terminal and appear the next message:

Couldn't set 1600x1200x0 video mode: No video mode large enough for 1600x1200

My monitor doesn`t have this resolution. So I try to uninstall and install again, but no results. How can I change the resolution or uninstall completely the freecraft?

Thanks

---

### Post by Flos-cuculi on 2006-08-04
I had the same problem, the answer is already posted in another thread.

In a terminal:
```
freecraft -h
```

Gives you a list of possible options. One of them:

```
freecraft -vX
```

Instead of the X place a number corresponding to your resolution.
1=640x480,2=800x600, 3=1024x768,4=1280x960,5=1600x1200
Freecraft should start in the right resolution.


Possibility n°2:

Edit the file preferences1.ccl in /home/.freecraft/ to match your resolution.

Enjoy

---

