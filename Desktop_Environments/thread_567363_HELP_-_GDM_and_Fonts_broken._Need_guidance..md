---
title: "HELP - GDM and Fonts broken. Need guidance."
date: 2007-10-04
forum: Desktop Environments
---

### Post by mrashley on 2007-10-04
So a computer that I don't have direct access to (only SSH and VNC) is on the fritz. When it turns on I have been told that X Windows loads up a graphic which then turns to a black background with the busy mouse cursor. (The cursor is movable and animated)

I ssh'd into the computer and found that GDM was at 99%. I couldn't figure out what was wrong and a dpkg-reconfigure gdm didn't fix the problem. I suggested using KDM instead as the login manager. I installed KDM and --purge removed GDM. 

Now the user is able to log in, however the fonts are all messed up. I've attached a picture of what it looks like. I don't know what on earth to do.

I looked in Xorg logs and there are only three mentions of missing fonts, and no other error messages that I can see.

Any thoughts?

---

### Post by mrashley on 2007-10-06
Help? Anyone please?

---

