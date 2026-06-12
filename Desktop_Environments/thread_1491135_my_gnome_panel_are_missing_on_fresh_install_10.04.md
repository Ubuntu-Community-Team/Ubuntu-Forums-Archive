---
title: "my gnome panel are missing on fresh install 10.04"
date: 2010-05-23
forum: Desktop Environments
---

### Post by lone_wolf45 on 2010-05-23
I have a problem with gnome panels, when i start ubuntu the gnome panels are missing. 

i have tried 

```
gconftool --recursive-unset /apps/panel
``````
rm -rf ~/.gconf/apps/panel
``````
pkill gnome panel
```which does restore the panels but if i reboot the panels go away again, please help

This is on a new installation of Ubuntu 10.04, i'm preparing it for use by someone else and they can't use it easily without the panels

---

### Post by jamesisin on 2010-05-23
I am seeing pretty much the same behaviour:

[http://ubuntuforums.org/showthread.php?t=1490250](http://ubuntuforums.org/showthread.php?t=1490250)

---

### Post by jamesisin on 2010-05-26
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/585659](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/585659)

---

### Post by c.brown on 2010-06-06
Having the same problem.

I just purchased a new Toshiba nb305, installed Netbook Remix and had panels until I ran Synaptic Package Manager (or at least I think that's when it happened).

I tried starting gnome-panel from the terminal, but get a "not installed" error.

Hmm...Any Ideas?

-Chris

UPDATE:

Gah! It seems that when I deleted Evolution it deleted my gnome-panel? Got my panels back after searching 'gnome-panel' in SPM, and that's when I noticed it had to load some Evolution dependencies. That all seems silly to me, but there it is.

---

