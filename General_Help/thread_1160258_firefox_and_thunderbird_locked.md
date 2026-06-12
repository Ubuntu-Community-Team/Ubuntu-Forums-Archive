---
title: "firefox and thunderbird locked"
date: 2009-05-15
forum: General Help
---

### Post by Richard-g8jvm on 2009-05-15
Hi

I can find my way around gnome without a problem.
this is my sons computer, he managed to really screw up the desktop.
I tried initially to add another user and copy the desktop files over..


failed

So I ended up moving all his files to the new user, adding the new
user to sudoers, and at the moment its updating to 9.04.


both firefox and moz thunderbird will not start , saying another instance is running.
ps ax shows they are not.

I've deleted .parentlock in both apps, and looked at the FAQ on mozilla.

I've tried both relative pathing in profiles.ini , still wont start..
I've tried starting both in -safe-mode, but it says firefox 3 not installed, ,,it is ...


susgestions ??
TIA



Richard

---

### Post by Richard-g8jvm on 2009-05-15
Found the thunderbird prob

as root in the /home dir "chown -R keith-2 keith-2/" doesn't work
some files are ignored ,

---

### Post by whoop on 2009-05-15
Did you try and remove ~/.mozilla ?

---

