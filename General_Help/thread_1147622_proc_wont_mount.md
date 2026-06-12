---
title: "/proc wont mount"
date: 2009-05-03
forum: General Help
---

### Post by clarusthedogcow on 2009-05-03
Earlier today, my computer stopped starting applications.  I tried starting them in the Terminal, but it just gave me a display not found error.  I figured it would be fixed by restarting, but when I did, i got a lot of /proc not found errors.  I was finally able to log in, but gdm could not start X, so it was just a command line session.  I logged in as root.  I tried mounting proc with "mount -t proc /proc" and I was given "block device proc is write-protected" followed by a mounting read only message, and a message that it couldnt be mounted read only.  I have since tried changing ownership and other similar things, but it doesnt recognize root as able to do these things.  If you have any insight or hints as to how to fix this, it would be good to hear.

---

