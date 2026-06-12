---
title: "revert to original splash screen"
date: 2007-01-19
forum: Desktop Environments
---

### Post by egypharaoh on 2007-01-19
Ok so im running Ubuntu 6.10 and i changed my splash screen with Gnome-Art.  Then i decided that i liked the old one more... how do i switch back?

---

### Post by Dave54 on 2007-01-20
This is a very good question and I would like to know the answer too.

You can install the gnome splashscreen manager from synaptic, this is what I use. however, it does not know the location of the original splashscreen. I think all it needs is the picture file to apply a splash screen, so if we could just find it we could restore the original splashscreen.

-Dave

---

### Post by paparucino on 2007-01-20
> **Dave54 said:**
> This is a very good question and I would like to know the answer too.

If you didn't remove anything you can run
```

sudo gdmsetup

```
then in the tab locale you should have to find your original splash screen, if you mean the screen where you log in
If this is not the case, let me know.

---

### Post by egypharaoh on 2007-01-20
> **paparucino said:**
> If you didn't remove anything you can run
```

sudo gdmsetup

```
then in the tab locale you should have to find your original splash screen, if you mean the screen where you log in
If this is not the case, let me know.

this is for changing the login screen... Im talking about the splash screen that comes on after you log in.  Its the one that has the little icons for whats loading... like nautalis and stuff.

---

### Post by raptor9k on 2007-01-21
look in /usr/share/pixmaps/splash  You should find what you're looking for.

---

