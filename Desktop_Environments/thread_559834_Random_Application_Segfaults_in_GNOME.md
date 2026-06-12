---
title: "Random Application Segfaults in GNOME"
date: 2007-09-25
forum: Desktop Environments
---

### Post by skastel on 2007-09-25
I've been running Feisty for a while with pretty good results on a few other PC's, but something is very amiss with one of them.  In the middle of normal use, programs quit unexpectedly with no error messages!
This happens with VMWare Server Console, Emacs 22, Firefox, Gnome-terminal, Rhythymbox and anything else that's running.  It's not consistent, some days are better than others.  If I run from a command prompt all I get is  a segfault when it finally dies.  Machine passes memtest just fine, and I'm not sure if there's a better place to look for more descriptive error logs.

My current setup is:
3.06 GHz Celeron
2GB DDR
160GB 7200RPM IDE
NVIDIA 6200 LE
Dual 22" Widescreen LCD's

Some help would be good, I'm getting pretty tired of having to re-launch applications just to have them mysteriously die again 10min. later.

---

### Post by skastel on 2007-10-03
I have no idea why no one is willing to even give a little advice on this.  I've seen a few other threads with similar topics, but none of them seem to ever have a resolution.  I'm going to try swapping out video cards and see if that helps. I'll post my results with different drivers/cards when I get some time.

---

### Post by skastel on 2007-10-04
So far so good today.  Been up for ~ 6 hours with no crashes.
Basically, I just installed Envy and upgraded to the newest NVidia proprietary drivers.  Everything went smoothly with the upgrade and I've been good this morning.  I'll post again tomorrow if it's definitely not crashing apps anymore.

---

### Post by skastel on 2007-10-16
Still crashing, new nvidia drivers with Envy helped at first, but after a few days, it started all over again.  Now I'm running xfce just to see if that would help but alas, still happening.  Firefox seems to be prone to the most crashes, but emacs-snapshot, vmware and rhythymbox all have 1 or more daily crashes.

I'm going to run the memory tester again, but it passed all the tests before with flying colors. *sigh* back to scratch on this one.

---

