---
title: "[SOLVED] How to switch login gui from Gnome-type back to Kubuntu"
date: 2008-12-21
forum: Desktop Environments
---

### Post by stir-crazy on 2008-12-21
Okay, I initially had Kubuntu installed, but added Ubuntu after upgrading to Intrepid because of many KDE issues.  At some point I let Ubuntu take over, being my primary session, including the login GUI.

Now, I'm happy with the KDE fixes, and want that sleek, oh-so-sexy KDE login manager to take over, but for the life of me, I can't find how to make this happen.  KDE is my default session now, but from the Gnome-type of login #-o.

How do I tell my machine that I want KDE to manage all login sessions, including the initial login?  Thanks!

Edit:  As usual, I just need to post a question in the forum before I find my answer on the same forum.  I'm a bonehead, sorry.  For other would be boneheads, here's the fix:

```
sudo dpkg-reconfigure kdm
```

---

### Post by stir-crazy on 2008-12-22
As I so often do, I spoke too soon.  Repackaging the login manager via ```
sudo dpkg-reconfigure kdm
``` seems to work, but when starting up the computer, both Gnome and KDM fail, and Netatalk takes over.

My /etc/x11/default-display-manager reads /usr/sbin/kdm

I don't see kdm in /usr/sbin; hidden or otherwise.  So, what do I do here to make the KDM login manager start as default?

---

### Post by abn91c on 2008-12-22
if you have kubuntu 8.10 go to system settings>advaned>login manager>theme

---

### Post by Zorael on 2008-12-23
kdm resides in /usr/bin/, at least in 8.10. In 8.04 KDE4 remix, the KDE4 kdm's name was kdm-kde4, much like every KDE4 app's name was postfixed with -kde4. It had its own little binary folder hidden someplace, its own little ~/.kde4 settings directory, etc etc, for the sake of compatibility with KDE3.

Perhaps you could manually alter /etc/X/default-display-manager to point to it, after having made sure to dpkg-reconfigure kdm?
```
$ locate kdm
```
Failing that, give it a good (**package**) reinstall.
```
$ sudo aptitude reinstall kdm
```

---

### Post by stir-crazy on 2008-12-29
Thanks for the replies.  It does seem to be fixed now, by editing the /etc/X11/default-display-manager to read "/usr/bin/kdm"  That's it, simple fix; at least one reboot now instigates a nice gui kdm login prompt.  Woulda' thunk that dpkg for this would have correcty reset it but not.  Anyway, fixed.

---

