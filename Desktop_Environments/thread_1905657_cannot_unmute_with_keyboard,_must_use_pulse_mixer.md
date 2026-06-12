---
title: "cannot unmute with keyboard, must use pulse mixer"
date: 2012-01-07
forum: Desktop Environments
---

### Post by davidism on 2012-01-07
Running Xubuntu 11.10.  When I refer to the mixer, I'm talking about pavucontrol.  Here is a scenario:

[LIST=1]
[*]Mute using keyboard button, volume is muted in panel and mixer.
[*]Unmute using keyboard button, volume is unmuted in panel, but still muted in mixer.
[*]or, unmute in mixer, everything is unmuted.
[/LIST]
So the problem is that the Pulse will not unmute, even though the panel reports that it is.


The most information I've found so far is that xfce-volumed is not meant to be used with Pulse. (So why are they both in use in Xubuntu?)


Is there anything I can do, some sort of ALSA or Pulse configuration, maybe a different mixer, etc., that will fix this?

---

### Post by SnickerSnack on 2012-02-07
I have the same problem, but no solution yet.

Edit: You might want to keep an eye on this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/912818](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/912818)

---

### Post by Sonador on 2012-02-08
Hi,

take a look at this, the post #2 solved it for me: 

[https://bugs.launchpad.net/xfce4-volumed/+bug/883485/](https://bugs.launchpad.net/xfce4-volumed/+bug/883485/)

---

### Post by SnickerSnack on 2012-02-08
Thanks for the link.  I'll try it later today.

Edit: I read the thread and decided to try post #3.  It worked perfectly.  Thanks again.

---

