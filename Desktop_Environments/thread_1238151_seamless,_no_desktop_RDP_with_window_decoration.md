---
title: "seamless, no desktop RDP with window decoration"
date: 2009-08-12
forum: Desktop Environments
---

### Post by RikoW on 2009-08-12
Dear all,

since a long time (in particular after upgrading to a new laptop and the most recent Ubuntu version), all seamless RDP windows show up with the Ubuntu desktop theme boarder.

I have a desktop PC with XP and a Dell E4300 with Ubuntu 9.04 (compiz+emerald). XP is set-up to run without desktop, so when starting a seamless RDP session for the explorer window, I get also the windows task bar at the bottom.

However, the task bar (and any other pop-ups and tool-tips) come up with the windows frame from Ubuntu. That was not the case before. I suspect, it has something to do with the compiz set-up but have no idea really.

Does anybody know how to fix that?

Thanks,

            Riko

---

### Post by Another Monkey on 2009-11-04
It's a known bug
[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/275528](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/275528)

From another post on here, "rdesktop" from Debian does not show the issue.  I am just trying to figure out how to install that.
[http://ubuntuforums.org/showthread.php?t=1095287](http://ubuntuforums.org/showthread.php?t=1095287)

---

### Post by RikoW on 2009-11-04
Actually, you can fix that yourself, as I found out:

[http://ubuntuforums.org/showthread.php?t=1277258]("http://ubuntuforums.org/showthread.php?t=1277258")

That worked in 9.04 and is still working in 9.10

Cheers,

     Riko

---

