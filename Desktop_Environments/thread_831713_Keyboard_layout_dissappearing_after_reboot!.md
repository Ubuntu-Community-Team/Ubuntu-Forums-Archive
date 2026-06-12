---
title: "Keyboard layout dissappearing after reboot!"
date: 2008-06-17
forum: Desktop Environments
---

### Post by Leav on 2008-06-17
Hi guys!

Weird problem here: I set up two layouts in the layout preferences (English US default and Hebrew) and selected Alt+Shift as the shortcut to switch between them.

that works great!

until I reboot.....

after that USA is default, alt+shift doesn't work, switching by hand doesn't work (i.e. clicking on USA changes it  to Isr, but it still enters my text in english) and the weirdest symptom of all:
if I right click on the "Keyboard indicator applet" and select "show current layout" it shows me a blank prompt, instead of a picture of the layout. (!)

after each reboot I can go to the keyboard preferences page, remove both layouts, add them again - and everything works great again - until the next reboot.

Any ideas?
Thanks!
-Leav

---

### Post by n_e_f on 2008-06-17
this is a known problem
the launchpad is here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)

there is a solution, try this:
[http://whatsup.co.il/index.php?name=PNphpBB2&file=viewtopic&t=45031&start=0&postdays=0&postorder=asc&highlight=nef](http://whatsup.co.il/index.php?name=PNphpBB2&file=viewtopic&t=45031&start=0&postdays=0&postorder=asc&highlight=nef)

hope it works for you

---

