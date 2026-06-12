---
title: "Multiple desktop problem"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by el escocés on 2007-11-20
I'm running Gustsy GNOME with compiz enabled and whenever I select a new desktop in the Workspace switcher panel it switches to a new blank desktop; no icons, menu bar, nothing.  I have to CTRL+ALT+BACKSPACE to get back into my main desktop.

I have disabled all compiz related desktop configurations and even tried it with compiz turned off but it still happens.

Any ideas?

---

### Post by Forlong on 2007-11-20
> **el escocés said:**
>  even tried it with compiz turned off but it still happens.
You're 100% sure about that?

Run ```
metacity --replace
``` and see if that solves the problem - if so, we can be sure it's a Compiz problem.

---

### Post by el escocés on 2007-11-21
You're right, it's a compiz problem.  Works fine when it's turned off.

---

### Post by Forlong on 2007-11-22
Alright, make sure the virtual desktops in Compiz are configured like described [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Getting the cube".

---

