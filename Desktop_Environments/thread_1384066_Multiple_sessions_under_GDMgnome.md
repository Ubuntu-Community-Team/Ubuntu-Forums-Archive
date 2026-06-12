---
title: "Multiple sessions under GDM/gnome"
date: 2010-01-18
forum: Desktop Environments
---

### Post by r_avital on 2010-01-18
Hi all, 

running Ubuntu Jaunty (9.04) 64-bit under gnome, display manager is GDM, uname-a returns:

Linux mymachinename 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux

When I was running KDM there was a simple way in KDE to start as many as 6 alternate graphical KDE sessions.  I'm trying to do the same thing in gnome running under GDM and having no luck.  All I'm getting is a notification that the server is already running.

I've tried Ctrl+Alt+Fx, but this with F1 to F6 gets me a console login, with F7 gets me the current session (as expected), with F8 gets me a screen with some output and no prompt, with F9 to F12 gets me a blank screen with blinking cursor.

I've read in another thread here (can't find it right now) that GDM does not support multiple sessions "out of the box" - does anyone know if this is correct, and if so, what would "out of the box" mean?

Also found some info about editing /etc/gdm/gdm.conf-custom, and using the follwing in the server section:

```
[servers]
0=Standard device=/dev/tty5
1=Standard device=/dev/tty6
2=Standard device=/dev/tty7
```I could adjust this to tty8, tty9 etc. all the way to tty12.  However this looks like it would load a new gnome desktop on separate displays, whereas I only have one display.  (again, this is feasible in KDM)

Would it be safe to assign them all to display 0?

Alternately, is there any other solution to this?

Thanks in advance :)

---

### Post by Barriehie on 2010-01-31
I've managed multiple sessions with gnome/GDM but for the life of me can't remember how I did it now.  It's what I'm searching on!  Here's a link regarding this [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674) , it's a bit dated but it's a starting point.

Barrie

---

### Post by Barriehie on 2010-02-01
Gottit in my thread [http://ubuntuforums.org/showthread.php?t=1394931](http://ubuntuforums.org/showthread.php?t=1394931)

Barrie

---

### Post by r_avital on 2010-02-02
Thanks so much, Barrie,

I read your thread and the threads that led to it from your links, and it's working for me, with two problems:

First, the fellow that gave you the solution, clearly says not to run X as root.  Well, when I try to run xinit as non-root, I get an error about permissions.  The only way to run it is with sudo.  And that logs me to the new session as root.

I suppose I could grant myself permissions to run xinit.

Second, I don't get as many sessions as I should  I only get sessions on Ctrl+Alt_F9, F10, F-11, and sometimes F12 (and of course the original session on F7).  Nothing on F8.  Sure, I'll never need that many, but I was simply researching the functionality.  

At any rate, thanks again for your solution, it answered my question.

All the best :)

---

