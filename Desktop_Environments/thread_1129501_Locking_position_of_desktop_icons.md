---
title: "Locking position of desktop icons"
date: 2009-04-18
forum: Desktop Environments
---

### Post by bunizz on 2009-04-18
Hi everyone,

I was wondering if there is any way to lock desktop icons on gnome desktop.

Does anyone know how to do it ?

Thanks.

---

### Post by Subito Piano on 2011-01-03
You can lock the desktop thru nautilus, which stops adding or removing anything to the desktop, but i am still trying to figure out how to lock the position.

---

### Post by rob2nd9th on 2011-02-09
Was after the same, and after much digging came up with this

```
gconf-editor
```

Apps > gnome-sessions > options and check the auto_save_session

I am on 9.04 - the Jaunty Jackalope

hope that helps got the idea from this

[http://ubuntuforums.org/showthread.php?t=429952&highlight=locking+icons+desktop](http://ubuntuforums.org/showthread.php?t=429952&highlight=locking+icons+desktop)

---

### Post by Krytarik on 2011-02-09
> **rob2nd9th said:**
> Was after the same, and after much digging came up with this

```
gconf-editor
```Apps > gnome-sessions > options and check the auto_save_session

I am on 9.04 - the Jaunty Jackalope

hope that helps got the idea from this

[http://ubuntuforums.org/showthread.php?t=429952&highlight=locking+icons+desktop](http://ubuntuforums.org/showthread.php?t=429952&highlight=locking+icons+desktop)
That is effectively the same as ticking "System -> Preferences -> Startup Applications -> Options -> Automatically remember...", but it remembers the last running apps also.

---

### Post by rob2nd9th on 2011-02-10
> **Krytarik said:**
> That is effectively the same as ticking "System -> Preferences -> Startup Applications -> Options -> Automatically remember...", but it remembers the last running apps also.

Lol well that a lot easer, could not find that last time I looked, but it is there must have had a moment. What I would like is to lock an Icon so that if you "clean up by name" any locked icons will stay where you want them.

---

### Post by jamibair1 on 2012-02-10
I am struggling with the same problem.
Please see these post's, where Lewis TM gave an answer.
[http://ubuntuforums.org/showthread.php?t=1919849](http://ubuntuforums.org/showthread.php?t=1919849)

My problem is, that I want the icons to be fixed, So that you are not able to move them around by accident.
LewisTM's answer gives the solution, but I am still new to Ubuntu. I can't even find out how to get to the dir and change attributes. LOL.

---

### Post by LewisTM on 2012-02-10
That answer was specific to XFCE. Maybe there is a similar trick to be done in GNOME, I don't know.
@jamibair1 : Are you sure you are running XFCE? That might explain why you can't find the directory :)

---

### Post by jamibair1 on 2012-02-11
Am using GNOME. That's why I couldn't do it, maybe. Should be more specific in my questions. Thank's :)
Wauw. Just discovered Xfce ! That's exactly what I'm looking for to my project.
Even if I have to install Xubuntu.
Thank you very much Lewis TM !

---

### Post by jamibair1 on 2012-02-12
Actually..
I worked a lot on the GNOME desktop already. Created personal icons for my project, trying to get to know the whole thing etc.
Is this a bug to be reported to the GNOMEteam or is there a solution ?
So far I found the file: ../desktop/gnome/file_views/icon_theme.
Does this have anything to do with "locking icons" ? If so, how to  chatrr this one ?
It would be nice, if there is a solution to this, as you can find in xfce. Am sure, others find this usefull too.
Any help much appreciated !

---

