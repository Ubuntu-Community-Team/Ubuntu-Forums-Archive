---
title: "[SOLVED] conky compositing difficulties"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by cardinals_fan on 2008-03-30
I am currently using the Xfwm4 compositor, but have seen this issue with both the new Metacity compositor and Compiz.  Every time my Conky updates, the desktop shows through any windows on top of it.  For example, when I am browsing in Firefox, ugly little patches of desktop appear through the Firefox window.  I could not grab a screenshot because any activity caused the patches to vanish.  Has anybody else had this problem?

---

### Post by aroch1 on 2008-04-01
Are you using the default conky settings or do you have your own .conkyrc set up?  If so, check the own_window_type variable, and set it to override.  This resolved a similar problem for me back when I was using conky.

---

### Post by cardinals_fan on 2008-04-01
> **aroch1 said:**
> Are you using the default conky settings or do you have your own .conkyrc set up?  If so, check the own_window_type variable, and set it to override.  This resolved a similar problem for me back when I was using conky.
I have my own - and it's on override already.

---

### Post by cardinals_fan on 2008-04-05
I've solved this.  Turns out that I needed a 'own_window_type desktop' line.

---

