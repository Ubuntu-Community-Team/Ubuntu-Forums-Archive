---
title: "Bionic Beaver 18.04 locks up when attempting to switch users"
date: 2018-10-09
forum: Desktop Environments
---

### Post by cybrsaylr on 2018-10-09
Installed BB, 18.04 LTS a week ago. Learning it, as is is a bit different from 16.04LTS which was used primarily before. 

Created another user account named 'Guest' which was on 16.04 by default and always worked fine. So now I have 2 users on  18.04. I can switch user and go into Guest and it seems to work fine. However when attempting to sign out of Guest and return to back my main user account 18.04 totally freezes/locks up! Mouse and keyboard are completely unresponsive, nothing works! This forces me to hold PC power button down doing a 'hard shutdown'. Then I restart PC all all runs fine until attempting to switch user again. Then all locks up again. Tried to remove the Guest user account but don't see how this can be done. Don't see any options for doing this.

Anyone have any idea on a fix to keep PC from locking up?

---

### Post by cybrsaylr on 2018-10-10
OK so I went into 18.04 Help section. Help section showed how to create and remove extra users. Removed the Guest user account created before and created a new user account. Switched over and went into this newly created user account. All ran fine. Then tried to sign out and go back to my main user account and PC froze and Locked up again just as stated in the OP! Had to do a hard shutdown again to restart PC. 

Can anyone HELP on this please?

---

### Post by cybrsaylr on 2018-10-11
Any ideas or HELP for this?

---

### Post by deadflowr on 2018-10-11
I think this is the bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1715365]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1715365")
Though the bug description isn't all that clear.

---

### Post by cybrsaylr on 2018-10-11
deadflowr,
Yeah it looks related to that bug. Looks like a Gnome bug? 
I liked Gnome before Ubuntu went to Unity but pretty much forgot about how Gnome ran....lol. Used Unity with 16.04 and never really had any problems with Unity, plus switching between users was never a problem. With 18.04 I'm pretty much struck using one user right now. Every time attempts are made to switch to another user, 18.04 locks up and keyboard and mouse become totally unresponsive! Nothing works forcing me to do a hard shutdown, by just pressing and holding the PC power button until PC shuts down, then doing a restart. 

Very annoying! Hope they make a fix on this.

---

### Post by cybrsaylr on 2018-10-18
Bump!

Anything being done to fix this bug?

---

### Post by QIII on 2018-10-18
If the bug referenced is the right one, I don't see anything in the report on Launchpad indicating what is being done.

Since nobody here works at Canonical, that's all we have to go on.

---

### Post by cybrsaylr on 2018-10-19
Always thought they read this board looking for issues to correct.

---

### Post by QIII on 2018-10-19
No.  The devs don't hang out here.  This is a user-to-user support forum.  We aren't employees of Canonical.

---

### Post by cybrsaylr on 2018-10-27
Bump!

Anyone have any ideas on this?

---

### Post by cybrsaylr on 2018-11-13
How is the best way to contact Canonical on this issue?

---

