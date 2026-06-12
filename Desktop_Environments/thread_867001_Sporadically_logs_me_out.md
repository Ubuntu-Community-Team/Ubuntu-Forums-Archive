---
title: "Sporadically logs me out"
date: 2008-07-22
forum: Desktop Environments
---

### Post by jtgalway on 2008-07-22
I am running Ubuntu 7.10 on a Dell laptop for the last couple of years and have had no problem with it until now. In the last couple of days I have seen strange behaviour and can't seem to troubleshoot it.

When I leave the laptop idle, eventually the screensaver starts up (I am using electric sheep). When I move the mouse pad, the screen starts to come back, then goes black and I get the log in screen! I just get logged out of the session. Usually, I only have a couple of emacs windows, a terminal and kdvi running (I'm working on a latex document).

I am not running compiz or any desktop effects. Strangely, it seems to only log me out when I go to move the mouse and this is a recent development. I haven't installed anything new recently, but I have upgraded firefox and a couple of things through update manager.

Does anyone know where I might begin to ascertain a bit more information on this problem. When I check /var/log/messages it just tells me that the session was restarted. The CPU isn't running overtime when it happens (not noticeably anyway).

Suggestions welcome.

---

### Post by kellemes on 2008-07-22
I posted the following thread in the Zenwalk forums some time ago, is it the same issue?
[http://support.zenwalk.org/viewtopic.php?f=10&t=13687]("http://support.zenwalk.org/viewtopic.php?f=10&t=13687")

You can bypass the issue by using non 3d-screensavers. Or get your 3d going, and see if the problem remains.
What videocard do you have and did you install a driver enabling the 3d stuff?

---

