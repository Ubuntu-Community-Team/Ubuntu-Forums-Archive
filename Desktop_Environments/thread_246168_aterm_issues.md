---
title: "aterm issues"
date: 2006-08-28
forum: Desktop Environments
---

### Post by gratuit on 2006-08-28
Hi, I'm having a problem running aterm. Whenever I try to run it I get the errors:
aterm: can't load color "White", colorID = 0, (29)
aterm: can't load color "White", colorID = 0, (29)
aterm: aborting

or if I try specifying another color:

~$ aterm -fg lightgray
aterm: can't load color "lightgray", colorID = 0, (29)
aterm: can't load color "White", colorID = 0, (29)
aterm: aborting

I can run this program in gnome, but cannot specify colors or it dies the same way. 
I have 
:~$ locate rgb.txt
/etc/X11/rgb.txt
/usr/lib/X11/rgb.txt

Any advice or pointers would be appreciated.
Thanks.

---

### Post by gratuit on 2006-08-28
Figured it out. With compiz apparently you have to symlink rgb.txt to /usr/share/X11/rgb.txt 

Putting RgbPath in xorg.conf does not seem to help.

---

