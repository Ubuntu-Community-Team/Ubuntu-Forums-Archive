---
title: "Gnome maximise window size"
date: 2009-04-22
forum: Desktop Environments
---

### Post by celticbhoy on 2009-04-22
How do I change the window size for a miximised window ???

What I mean is if I press the maximise button on a window how can I set the size it goes to.

---

### Post by celticbhoy on 2009-04-22
I have attached a screenshot to show why this is a problem for me, the firefox window shown has been maximised, but stop's short of covering the lower part of the screen. I think this happened after I installed AWN, but I aint 100% on that. I had a look in gconf but nothing obvious jumped out at me. I use Compiz & Emerald in case that makes a difference.

Any ideas ............
:confused:

---

### Post by celticbhoy on 2009-04-22
Oops forgot screenshot....
:redface:

---

### Post by celticbhoy on 2009-04-24
OK I have discovered the cause of the problem, AWN. For some reason gnome see's the max area size as the top of AWN when it is on screen so I dont get the use of the bottom of the screen. I just need to know how to fix it. Is there a setting in AWN maybee???

---

### Post by MaskedMarauder on 2009-04-28
You get the same thing with kde.  Its bloody annoying.  I get notification windows the size of a house with two teeny lines of text!


FOUND IT!

There's a package called 'devilspy' which lurks in the background and kidnaps any new window and processes it.  Apparently maximize is its default behaviour.  I removed the package and everything's fine now.

---

