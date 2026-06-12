---
title: "firefox does nothing"
date: 2009-02-11
forum: Desktop Environments
---

### Post by wateenellende on 2009-02-11
Firefox has just mysteriously died. It doesn't do *anything* anymore.

If I start it, I just get a blank window: no "file edit etc " menu, just all gray. WTF?

I already removed the entire .mozilla dir - no change. It's a 8.10 install, fully patched. Idea's, anyone?

---

### Post by Triptol on 2009-02-11
You could try starting it from the command line (in a xterm or so). See if you see any errors.

---

### Post by wateenellende on 2009-02-11
lucifer@XWing:~$ firefox
lucifer@XWing:~$ firefox -v
Mozilla Firefox 3.0.6, Copyright (c) 1998 - 2009 mozilla.org
lucifer@XWing:~$ 

Still does absolutely nothing - just forks to the background and leaves an empty window. Adding the -v makes it exit after printing the version string.

---

### Post by thompson42 on 2009-02-12
Is there a horked-up copy of firefox running but not visible?

ps -ef | grep firefox

If so, killall firefox, then repeat the ps command to be sure it's gone, then restart firefox.

---

### Post by jrusso2 on 2009-02-12
Are you sure you have a working internet connection?  What have you installed or changed recently?

---

### Post by tlois on 2009-02-21
Thank you, Thompson!  I was having the exact problem.  I had to install foxmarks, but all my stuff was there.  Very strange, though, absolutely nothing was working- not even the back buttons.

Thanks again.

---

### Post by keithld on 2009-02-21
Have you tried safe mode???

firefox -safe-mode in a terminal...

---

