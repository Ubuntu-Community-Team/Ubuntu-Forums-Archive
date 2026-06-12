---
title: "Sound events are not happening?"
date: 2009-02-01
forum: General Help
---

### Post by gbrethen on 2009-02-01
I have set 'Play alerts and sound effects' and when I test them in the sound panel, they work, but when I close the sound panel, the events don't play?

Help please!

---

### Post by gettinoriginal on 2009-02-01
Are you running 8.10 ??  If so, continue:
There has been a problem on some systems, try this.  Add these to third party software in Software Sources: (System, Administration, Software Sources)  Add them seperately.  You should copy and paste to avoid problems.
```
deb http://ppa.launchpad.net/gkulyk/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/gkulyk/ppa/ubuntu intrepid main
```

Once they are entered, it will tell you that you need to reload, go ahead and do it.  Then reboot, and it should show that you have updates.

By the way, welcome to Ubuntu  :p

---

### Post by gbrethen on 2009-02-02
Thanks!  That was the cure...

---

