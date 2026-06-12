---
title: "window title bar disappears when maximized"
date: 2009-03-06
forum: Desktop Environments
---

### Post by green69 on 2009-03-06
Hi everybody!

I have ubuntu 8.1 on an acer aspire one notebook and I installed it exactly how is reported on the ubuntu guide. Since last week everything was ok andeverything was working perfectly. 

Then, I think after an actualization (but I'm not sure) I started experiencing a problem in the desktop environment. Now, everytime I maximize a window (every types of window), window title bar (including minimizing and close buttons) disappears under the top pannel.

Can anybody help me with this? Or have you an idea on why does it pass? This is quite annoying and I need to solve it.

Thank you in advance for you help!

---

### Post by bapoumba on 2009-03-06
[http://ubuntuforums.org/showthread.php?t=757234](http://ubuntuforums.org/showthread.php?t=757234)
Please have a look, hoping it will help :)

---

### Post by binbash on 2009-03-06
did you try

compizconfig settings manager > workarounds > untick legacy fullscreen support

---

### Post by green69 on 2009-03-06
I tried this...
> **binbash said:**
> did you try

compizconfig settings manager > workarounds > untick legacy fullscreen support

... but it doesn't work. I even followed the link above but: same problem -> no solutions!

---

### Post by t1s on 2009-03-18
i'm having this exact issue. the windows look fine as long as I'm not maximizing them and i've tried unticking the legacy fullscreen as well as the link posted in the first reply.
any more suggestions?

---

### Post by t1s on 2009-03-22
I was able to figure my problem out with this thread:
[http://forum.eeeuser.com/viewtopic.php?id=44465]("http://forum.eeeuser.com/viewtopic.php?id=44465")
Turns out maximus had been installed on my machine.

sudo apt-get remove maximus

and reboot, seems my problem is solved now

---

