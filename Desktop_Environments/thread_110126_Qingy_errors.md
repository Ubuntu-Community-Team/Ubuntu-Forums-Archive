---
title: "Qingy errors"
date: 2005-12-30
forum: Desktop Environments
---

### Post by trevorv on 2005-12-30
As I use Xfce, I thought I'd replace GDM with something more lightweight, and decided to go for Qingy. I'm getting the following error though;

```
Unrecoverable error: reverting to text mode!
```

So I ran qingy tty1 -v | less

And after it adds keybindings, it spews up;

```
Session locking is NOT enabled
Native theme resolution is '1024x768'
framebuffer resolution is '640x480'
qingy: fatal error: could not create temporary file!
```

If anyone could help me solve this I'd appreciate it!

---

### Post by trevorv on 2005-12-30
Hmm, I seem to have gotten rid of that error (not quite sure how, heh) and now get "Segmentation Fault".

Any suggestions?

---

### Post by SigmaX on 2006-02-11
Not sure about the seg fault, but the first error is most likely because you're not running it as root.

All the same Qingy gave me grief with DirectFB when I tried to install it... I gave up after an hour or two.

SigmaX

---

