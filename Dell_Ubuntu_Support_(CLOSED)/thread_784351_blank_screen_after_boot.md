---
title: "blank screen after boot"
date: 2008-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mc-laptop on 2008-05-06
I've installed ubunstudio hardy on my Dell Latitude d430. Machine boots into a black screen. 

I've no problems booting in "recovery mode"

Has anyone an idea how I can solve/find the problem?

---

### Post by bobblehat on 2008-05-06
I can't suggest a fix as yet but in case it helps, it sounds similar to something I'm trying to diagnose here -> [http://ubuntuforums.org/showthread.php?p=4896011](http://ubuntuforums.org/showthread.php?p=4896011)

Out of interest, in recovery mode if you run 'startx' do you get a desktop up?

---

### Post by bobblehat on 2008-05-06
(sorry - timeout caused double post)

---

### Post by bobblehat on 2008-05-06
I just found this thread (hadn't seen it previously because I was searching for Skulltrail and 8800 GTS problems after many successful installs on other hardware - your post made me search more generally for boot problems).

[http://ubuntuforums.org/showthread.php?t=121819](http://ubuntuforums.org/showthread.php?t=121819)

---

### Post by mc-laptop on 2008-05-06
I've tried your suggestion but it did not work. My problem is slightly different because I do not hear the 'welcome' sound after boot.

The machine boots with splash screen and then I get a flurry screen. First with some 'red color shower' and then the whole screen gets flurry. I can't even switch into text mode with [Strg]+[Alt]+[F2]

Boot with 'recovery mode' still works fine.

---

### Post by bobblehat on 2008-05-07
There's a chance you're seeing something entirely different but in case it helps you might find the instructions for removing 'quiet splash' from the boot options useful towards the bottom of this page -> [http://ubuntuforums.org/showthread.php?t=756708&page=2](http://ubuntuforums.org/showthread.php?t=756708&page=2)

---

### Post by mc-laptop on 2008-05-07
I found the problem. After re-installing Hardy I've played around with the ubuntustudio theme. If I install usplash-theme-ubuntustudio then the machine can not boot properly anymore. After I've uninstalled the usplash-theme I could boot properly.

I think I'll post a bug report on this issue.

Anyway, thanks for your generous help. It was highly appreciated

---

### Post by bobblehat on 2008-05-12
No problem. Glad you fixed it.

---

