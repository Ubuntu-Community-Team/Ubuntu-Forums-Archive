---
title: "X/gdm worked fine, reduced resolution no change to xorg.conf"
date: 2008-05-30
forum: Desktop Environments
---

### Post by chardson on 2008-05-30
Greetings,

Our shared work machine (running 8.04) reverted to a failsafe xorg.conf recently and I can't get it back into the prior mode.  The xorg.conf was created on 5/01 and worked at full resolution for almost a month with our Dell 2007wfpb monitor.  On 5/27 (when the resolution reverted to 800x600 or 640x480), a few files showed up:
[INDENT]/etc/X11/xorg.conf.failsafe
/var/log/Xorg.20.log
/var/log/gdm/:20.log
/var/log/gdm/failsafe.log[/INDENT]

None of these files seem to mention any errors, and a diff between Xorg.20.log and an older log did not give any hints (only two lines differ, date and virtual term chosen).  gdm's failsafe.log only contains  ```
1211893847 9dd2a68cd4838eb76ef5d2d999952b3e  /etc/X11/xorg.conf
``` (which I don't know how to read)

The xorg.conf does not specify screen resolutions, I realize that I could edit them manually, but I'm wondering if anyone has any insight into what happened.  I have also tried changing the session to regular gnome (in case it was in failsafe) and killing X (ctrl+alt+bkspc), to no avail.

I've tried googling for this but didn't find much.  Also for the gdm failsafe.log, but most of those hits are from people who were messing with xorg.conf, while we were not.

Any thoughts? Insight would be appreciated.

-chardson

---

### Post by chardson on 2008-05-30
Solved.

The recent kernel update needed to be followed by a reinstallation (or something) or the  restricted driver manager with nvidia drivers.

-chardson

---

