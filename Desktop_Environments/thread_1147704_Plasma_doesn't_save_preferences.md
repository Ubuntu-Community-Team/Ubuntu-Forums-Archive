---
title: "Plasma doesn't save preferences"
date: 2009-05-03
forum: Desktop Environments
---

### Post by marciovinicius on 2009-05-03
Notifications and widgets from Plasma doesn't save my preferences.

Two examples:
1- I put a system monitor widget... I configured (via "preferences" in right-click menu) to show only what I want and another minor configs. But when I restart the PC, all preferences are lost.

2- In kopete, I choose not to show popups... But Plasma simply ignores all configs from Kopete.

What can I do to make Plasma remember my preferences?

P.S.: I am used to Gnome, i decided to adopt KDE (now with kubuntu 9.04) because I always felt KDE is more relyable and, mainly, more configurable. I'm still learning.

P.S.2: I use Brazilian Portuguese version of Kubuntu, so the names I wrote here may be wrong.

---

### Post by chrisrhode on 2009-07-30
I'm also having the same issue - and alas I haven't found a solution on the forums yet.  Have you had any luck figuring out the issue?

---

### Post by marciovinicius on 2009-07-30
Try to start with [this on Kubuntu forums]("http://kubuntuforums.net/forums/index.php?topic=3102737.0"), I think it is a related problem. Anyway, It didn't work for me. And after someone said me it isn't worth to solve this problem, I simply gave up.

I'm already planing to back to ubuntu (Gnome) on next release. Some day I'll be back to KDE when they make KDE4  trustful. There're still too many bugs and the new programs selection is too poor (i mean with poor programs).

---

### Post by Zorael on 2009-07-30
Permissions issue?
```
$ sudo chown *yourusernamehere*:*yourgroupnamehere* ~/.kde* -Rv
$ sudo chmod 0600 ~/.kde/share/config/plasma* -v
```

Borked settings files?
```
$ kquitapp plasma-desktop
$ mkdir ~/plasmabackup
$ mv ~/.kde/share/config/plasma* ~/plasmabackup
$ plasma-desktop &
```

(Omit the dollarsigns; they're code convention to show those are terminal commands.)

---

