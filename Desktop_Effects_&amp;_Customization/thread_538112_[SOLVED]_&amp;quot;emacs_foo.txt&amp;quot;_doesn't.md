---
title: "[SOLVED] &amp;quot;emacs foo.txt&amp;quot; doesn't open foo.txt"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by digidocs on 2007-08-29
Up until about a week ago typing "emacs foo.txt" would bring up emacs with foo.txt loaded.  Now, typing that will bring up emacs with no file loaded, as if I had just typed emacs.  I then have to press a key or click to get the file to display.  

This is very annoying, what do I do?  This is emacs22 in feisty.

Thanks for the help,
-DC

---

### Post by bashologist on 2007-08-29
Use the --no-splash option? Make an alias?

---

### Post by digidocs on 2007-08-30
You are my hero for today!  --no-splash fixed it.

To prevent having to type --no-splash every time I start emacs I added the following to my .emacs file.

(setq inhibit-startup-message t)

Thanks again for your help.
-DC

---

