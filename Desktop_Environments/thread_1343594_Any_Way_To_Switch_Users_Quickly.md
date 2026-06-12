---
title: "Any Way To Switch Users Quickly?"
date: 2009-12-02
forum: Desktop Environments
---

### Post by machineghost on 2009-12-02
My girlfriend and I share a computer, and whenever we "switch users" (IRL) we also "switch users" (in Linux terms).  Going back to the login screen every time is a nuisance (albeit a minor one).  Is there any way I can add a shortcut to my/her taskbar that would let us switch directly (password protection isn't an issue for us) with only a single click (maybe by invoking a shell script of some sort)?  If not, what's the next fastest (least clicks required) way we can switch?

(I tried the fast-user-switch-applet but it doesn't seem any faster to me; it too just has a "Switch User" option, which sends you back to the login screen.)

---

### Post by akudewan on 2009-12-02
One way would be to keep both users logged in and switch using Ctrl+Alt+F7 and Ctrl+Alt+F8. That way, you have to see the login screen only the first time for each user. Unfortunately, it would also eat your RAM a bit.

---

### Post by Hero of Time on 2009-12-02
You can use a face-browser login theme for GDM, that should allow you to switch uses through the applet, click the username, then type the password and you're done. Same idea as on Windows XP and newer with the welcome screen.

---

### Post by machineghost on 2009-12-05
Thanks for the suggestions!  I had hoped there might be some command I could use to do the user-switch, along the lines of su=>gksu=>(gkgnomesu? gksugdk?).  I guess we'll just have to go through the login window every time (but thanks to the face browser at least we won't have to retype our usernames) :)

---

