---
title: "X server won't run"
date: 2009-03-04
forum: Desktop Environments
---

### Post by metalhead0010 on 2009-03-04
When I tried to boot my laptop I was given an error message that said "Ubuntu running low graphics mode" and I canceled, logged in, and used startx and I got another error message that said
 "Saw Signal 11.  Server aborting.
giving up.
xinit:  Connection refused (errno 111):
xinit:  No such process (errno 3):
xauth: error in locking file ~/.Xauthority"
Thanks in advance, if I get any help that is, which I won't.

---

### Post by metalhead0010 on 2009-03-05
I know why the x server won't run (sorry I didn't mention it) it's because it thinks no display is set.  How do I set it, and I already tried xorg.conf.

---

### Post by metalhead0010 on 2009-03-06
I want you all to know that you were all of no help at all, and you never will be.  Already I have about 35 views and no one replied, that's either because A: you don't know how to fix it; or B: you don't want to help.  I should probably just try to fix it myself; even if I make the situation worse it's better then sitting around for an answer all day.

---

### Post by shankru85 on 2009-03-06
Mind telling a few details about the configs of your system? Btw, i may not be of any help to you since i am also a kinda noob. Probably that would be a starter for the others to start helping you.

Anyway instead of directly changing xorg.conf file, could you try using xorgconfig or other slightly graphical xorg configuration tools to set xorg.conf?

---

### Post by metalhead0010 on 2009-03-07
Thanks for answering but I did configure it automatically.  I'll try to post the output of the lshw command or whatever the command is.

---

### Post by metalhead0010 on 2009-03-11
I found out why X won't start.  I'm using a radeon V200 (I think) and I installed fglrx driver for ati which conflicted with the preindtalled drivers.  I'm going to delete fglrx and see what happens.

---

