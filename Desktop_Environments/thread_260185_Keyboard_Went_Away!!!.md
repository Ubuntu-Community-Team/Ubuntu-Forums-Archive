---
title: "Keyboard Went Away!!!"
date: 2006-09-18
forum: Desktop Environments
---

### Post by bobmct on 2006-09-18
:confused: Oh Boy!!!
I've been using Ubuntu (actually Kubuntu) on my work desktop for a couple of weeks now with pretty good results.  I even have dual-heads working well.
Last Friday in the middle of the day while doing something else, all of a sudden my keyboard stopped responding.  Nothing, NADA, zilch!!!  The first thing I suspected was 1) cables then 2) keyboard failure.  NOPE!

I've spent the better part of the past few days trying to get this working again.  Here are my current symptoms (results the same for both kdm and gdm):

At the gui login the kbd works.  I can enter my username and pwd and it is accepted.  Goes through the normal desktop startup and when the desktop is displayed, the kyb doesn't work!  Anything requiring keystrokes or keypresses dont respond.

The mouse works and I can right click and log out which returns me to the gui login prompt.  If I select the "console terminal" option the gui goes away and I am presented with the console prompt.  The keyboard works.  If I login as myself then key "startx" and the desktop gets displayed... no keyboard again.  However, if I login as root at this level then key "startx" when the desktop is displayed the keyboard WORKS.

So, I assumed the issue must be related to a configuration or a startup script somewhere.  I set about to trace/track/compare and even copied virtually all I could find from /root/ to my own home and changed the owner/group values.  Exact SAME results.  NO KEYBOARD!

Has anyone experienced this before?  If so, can anyone respond with what they did to resolve it?  I just want to resume my daily work!!!

Any other ideas will be most gratefully appreciated.

Thank you.

Bob ](*,)

---

### Post by bobmct on 2006-09-18
[COLOR="Red"]Anyone???[/COLOR]

---

### Post by editrix on 2006-09-21
You've probably already seen this thread, but in case not:

[http://www.ubuntuforums.org/showthread.php?p=1527367](http://www.ubuntuforums.org/showthread.php?p=1527367)

Wish I could help, but at least you know you're not alone. :-)

---

### Post by Scheater5 on 2006-09-21
Yup - that would be my thread in the link above.  Try holding a key in KDE and see if the repeat works.  1) that would imply we have the same/similar problem 2)you can actually type that way, by repeating and then deleting very carefully, annoying and tedious as it may be.  
Do let us (and ME!!!) know if you come up with a fix.

---

