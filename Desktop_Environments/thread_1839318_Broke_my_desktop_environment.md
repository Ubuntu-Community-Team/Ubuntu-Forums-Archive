---
title: "Broke my desktop environment"
date: 2011-09-05
forum: Desktop Environments
---

### Post by Johnny Buffalkill on 2011-09-05
So I keep a natty installation on an external HD that I tinker with.  I usually use ubuntu classic, but I was playing with Unity and tried activation the rotating cube (maybe I shouldn't have done this in Unity).  Anyway my desktop completey froze as soon as I did this and I had to do a hard shutdown.  Afterward, neither ubuntu classic nor Unity will load properly.  I only get my wallpaper image and a mouse pointer.  I can then ctrl-alt-F1 to a shell, but I don't know what to do there.  I can also go into ubuntu safe mode.  There I tried resetting ccsm to defaults and some package repairs, but I still can only log into safe mode.  Any ideas on what I should try to fix this?

---

### Post by raja.genupula on 2011-09-05
[http://tombuntu.com/index.php/2008/02/08/starting-and-stopping-gnome-from-the-command-line/](http://tombuntu.com/index.php/2008/02/08/starting-and-stopping-gnome-from-the-command-line/)

from that first stop gdm and the start it again from terminal  

if it is done & still have the problem with the unity . then do this 

```
unity --reset
```

all the best .

---

### Post by Johnny Buffalkill on 2011-09-05
Thank You Raja!  That did the trick.

The magic combination was to drop into a shell with ctrl-alt-F1.  Then from the first link:
```
sudo /etc/init.d/gdm stop
```Then:
```
unity --reset
```Once I did this I could log into unity.  From Unity, I could play with the login screen settings and then get into gnome/ubuntu classic.  

Also, I see that there is another thread with the same issue, posted at almost the exact same time, cause by playing with compiz in Unity.  Maybe compiz and unity don't mix?

---

### Post by Krytarik on 2011-09-05
If you still want to enable the Desktop Cube in Unity, please see this guide:

[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by raja.genupula on 2011-09-05
> **Johnny Buffalkill said:**
> Thank You Raja!  That did the trick.

The magic combination was to drop into a shell with ctrl-alt-F1.  Then from the first link:
```
sudo /etc/init.d/gdm stop
```Then:
```
unity --reset
```Once I did this I could log into unity.  From Unity, I could play with the login screen settings and then get into gnome/ubuntu classic.  

Also, I see that there is another thread with the same issue, posted at almost the exact same time, cause by playing with compiz in Unity.  Maybe compiz and unity don't mix?


aah i am very glad that you have solved your issue .

---

