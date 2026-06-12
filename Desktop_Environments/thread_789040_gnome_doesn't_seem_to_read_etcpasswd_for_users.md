---
title: "gnome doesn't seem to read /etc/passwd for users"
date: 2008-05-10
forum: Desktop Environments
---

### Post by nightfrost on 2008-05-10
Since the last set of updates (yesterday) from the -proposed repo, GNOME seems to fail to read /etc/passwd for users, or something like that. The GDM face browser shows no users, and the fast-user-switch-applet only shows the user logged in. How could I login you ask? Well, even though no users are shown in GDM, it works just fine to write the username and password to login. 

What gives?

---

### Post by bapoumba on 2008-05-10
Which package from -proposed?
These repos are for testing packages, usually to fix bugs, before they hit the main repos and updates.

---

### Post by nightfrost on 2008-05-10
> **bapoumba said:**
> Which package from -proposed?
These repos are for testing packages, usually to fix bugs, before they hit the main repos and updates.

Yeah, I know. I was hoping to be one of the brave ones who would let the staff know about potential problems, but I blindly updated this time. I have another machine which I haven't updated yet, and the packages from -proposed that are ready to be installed there, are amongst others: evolution & a bunch of libs., bash, gnome-desktop-data, gnome-settings-daemon (the change log for these last two indicates trivial changes "make the background  changes work when not using nautilus lp #214347), gnome-system-monitor, hal, libgtk, updatemanager.

So, I can't see what might have caused the problem...

---

### Post by Jst on 2008-05-11
Downgrading bash solves the problem, so there must be a problem with bash.

---

### Post by bapoumba on 2008-05-11
There are several bugs related to bash in Launchpad, maybe this one?
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931")

There is a workaround:
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931/comments/2]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931/comments/2").

---

### Post by nightfrost on 2008-05-11
Ah, thanks! I did search for it at launchpad but didn't find anything there.

---

