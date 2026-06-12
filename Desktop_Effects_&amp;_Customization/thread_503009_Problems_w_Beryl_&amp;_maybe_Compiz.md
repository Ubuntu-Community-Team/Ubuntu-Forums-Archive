---
title: "Problems w/ Beryl &amp; maybe Compiz"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by UltimateGordita on 2007-07-17
Okay, I've been searching the forum for a while now but most things seem to apply to ATI AIGLX and that kind of thing.

I'm trying to get Beryl up and running on XGL and I have all the required software (so far as I know).

Running

```
glxinfo | grep render
```

yields a yes to "Direct Rendering" normally, and while running Xgl session no. (If that matters)

The details are when running beryl-manager I'm able to switch my Window Manager to beryl, but nothing occurs, Metacity settings remain.  I can switch to Compiz and the effects start but there are absolutely no title bars for any running applications. If I try to switch back from Compiz to Metacity I get Whitescreened and have to Ctrl Alt Backspace or reset out of it.

Running $ beryl-manager in console I get...

** (beryl-manager:<ID>): CRITICAL **: can't execute beryl-xgl: Success

Which is repeated indefinitely.

And if I try $ beryl in console I get Whitescreened and can't view console output.

I'm using GeForce 7300GT 256MB P5B Plus MB (If that helps)

Included is my xorg.conf

Help is appreciated, thanks. :)

**Edit:** Thought I might add I'm running feisty and as far as I know my drivers are installed properly (but I don't know for sure how to verify that).

---

