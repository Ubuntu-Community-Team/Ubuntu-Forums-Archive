---
title: "Gnome has a five minute lag on logout/login"
date: 2007-07-08
forum: Desktop Environments
---

### Post by Frem on 2007-07-08
My copy of Ubuntu 7.04 has this problem. It's actually been affecting me since 6.06 was first released, but it's starting to get annoying.

Basically, when I log out of Gnome, if I log back into Gnome, there will be a five minute lag when the computer just sits there not doing anything, not loading Gnome, not giving me a desktop, no disk activity, nothing.
If I log out of Gnome and then log into XFCE, I won't be able to start any Gnome apps like Rhythmbox or Tomboy for about five minutes after login.

So, if I log out of Gnome and then log back in, it will sit there for between three to five minutes with the brown screen, but no loading window. About midway through, a gray rectangle appears in the upper right-hand corner of the screen. When the desktop finally loads, the gray rectange turns into a window and text appears in it. This is what it says:> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Can someone help me make my logins not have this five minute pause?

edit: This is the output of "ps x" from tty1 while gnome login is lagging.
```
  PID TTY      STAT   TIME COMMAND
 5227 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
 5329 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.10 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=23
20981 ?        Ss     0:00 /usr/bin/gnome-session
21026 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
21029 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
21030 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
21032 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 6
21035 ?        S      0:00 /usr/bin/gnome-keyring-daemon
21037 ?        Sl     0:00 /usr/lib/control-center/gnome-settings-daemon
21065 tty1     S      0:00 -bash
21067 tty1     R+     0:00 ps x
```

---

### Post by kfrance on 2007-07-10
I'm having the same problem anytime I try and log in.  It just started happening a few days ago.  I'll keep watching this post to see if anyone has answers.

---

### Post by Marchard on 2007-07-11
Me too Facing Similar 
[http://ubuntuforums.org/showthread.php?t=498909](http://ubuntuforums.org/showthread.php?t=498909)

---

### Post by Frem on 2007-07-19
Now, Gnome is starting to load up (the first time) with an error about "Expecting a keyboard with 101 keys, but found a 105 key layout instead. [Use X settings] [Use Gnome settings]"

Never seen it before.

---

