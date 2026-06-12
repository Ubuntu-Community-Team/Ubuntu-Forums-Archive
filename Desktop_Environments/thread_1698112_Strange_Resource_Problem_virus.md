---
title: "Strange Resource Problem virus"
date: 2011-03-01
forum: Desktop Environments
---

### Post by Jefferythewind on 2011-03-01
**Solved**

Once I restarted the computer the problem went away.  That was strange, but the posts below were very useful.

**Solved**

Hi Everyone,
  I seem to have got some kind of virus. I did recently install a package of updates, but I have no idea if this is the problem.  I have attached a picture that explains the whole problem.  My computer freezes a 5 seconds for about 2 seconds.  Does anyone have any idea what could be causing this?  
  In my active processes list, nothing jumps out at me.

Thanks

---

### Post by Frogs Hair on 2011-03-01
Run ```
top
``` in the terminal and see if you find out what process is causing it.

---

### Post by Jefferythewind on 2011-03-01
Thanks Frogs Hair,
  That is a very useful command that I didn't know about.  It seems that a command called 'events/l' is eating up all the processor.  It is funny because this process does not show up on the Gnome-system-monitor process list.  
  I did a google search and didn't find anything distinctive.  Does anyone know about this, or how I can try to kill this?

  Thanks a lot.

---

### Post by Piccy on 2011-03-02
A bug was reported for this about 5 years ago

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/67126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/67126)

May be of help

---

### Post by Jefferythewind on 2011-03-02
Piccy thanks for the help.  I will turn to this bug report for more help in the future.  It looks like this is the same bug that I have, although i am not using the same kind of wireless card mentioned in the bug report. Since restarting my computer it seems to have gone away though.  Now the 2 cores of my CPU are alternating from 3% to 20%, which is much better.  And this event/1 does not show up in the top report.

---

