---
title: "Screwed up user login...help!"
date: 2007-09-03
forum: Dell  Ubuntu Support
---

### Post by tyraeon on 2007-09-03
This was a stupid move of me, and I regret it.

Basically, I wanted to change my username (we'll call it X) to a different username (Y). I went into System>Administration>Users and Groups and selected X's properties and changed the username to Y. Without thinking, I decided "hey, I want to change the directory to /home/Y. *stupid*

So I log out, and upon logging back in, when I try to log in using username Y and password for Y, it says "the folder /home/Y does not exist. Run in failsafe mode." Regardless of what mode, failsafe or not, I log in with, it boots me out saying "This session was under 10 seconds long." It won't let me log in as root, either. "The system administrator may not log in through this window."

Has this happened to anyone? Halp plz, I need Ubuntu :[

---

### Post by Afishionado on 2007-09-03
Can you boot from the CD and get a desktop?

Try opening up [your hard disk]/home and rename the folder "X" to "Y".

Reboot, cross your fingers, and see if you can log in again.

---

### Post by tyraeon on 2007-09-03
I am running bootable cd now...I can't find my /home/Y folder. When I go to Places>Computer>/home all that is in there is /ubuntu. :[

If I go to System>Administration>Users and Groups, all that is there is root.

Any idea on where to go from here? Thanks.

---

### Post by gsiliceo on 2007-09-03
You need to mount the hard disk, try installin disk manager and then start nautilus as root
> sudo nautilus
then rename your dir

[http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)

---

