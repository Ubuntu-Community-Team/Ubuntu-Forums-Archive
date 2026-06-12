---
title: "Apply specific Compiz effect on each startup (Negative)"
date: 2009-10-05
forum: Desktop Environments
---

### Post by anarkhos on 2009-10-05
I have Compiz running smoothly.  After each startup I'd like the colors to be inverted by default, which is done with the Compiz `Negative` filter.

How can I apply compiz filters automatically on startup?

---

### Post by tsger on 2009-10-05
Are  you using the compizconfig-settings-manager?

---

### Post by anarkhos on 2009-10-05
Yes, Im using the CompizConfig Settings Manager.  Is there an option in it to make current settings active after reboot?

its not a big deal in the least, because all I must do is type Super+M to invert colors.  Its so quick, yet I'd still like to know how I can have gnome do this for me each login.

---

### Post by oldarney on 2011-04-13
I am having this same problem and would really love an answer.

---

### Post by Copper Bezel on 2011-04-13
Well, it's an action, not a setting, so you can't make it persist in Compiz itself. (I'm curious what nefarious purposes this is being put to. = )

The simplest way would be to install the package lineakd from the repos and make a startup application for the command xsendkeys Super_L+m . It'll run the keystroke for you, although it's possible that it might try running it too early, before Compiz can capture it, and you might have to delay it.

---

### Post by anarkhos on 2011-08-06
> **Copper Bezel said:**
>  (I'm curious what nefarious purposes this is being put to. = )


Inverted colors are easier on the eyes.  Have you tried it before?

---

