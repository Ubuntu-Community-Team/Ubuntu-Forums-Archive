---
title: "Unable to unlock desktop once locked (12.04)"
date: 2014-05-06
forum: Desktop Environments
---

### Post by flippo on 2014-05-06
Hello,

In summary my issue is that I'm able to log-in to the lightdm login screen, but once I've logged in, I'm unable to unlock my machine once the screensaver and autolock screen come up.  I'm unfamiliar with what suite ubuntu uses to control the screen locking/unlocking, so I think I'll need some help in deciphering exactly whats broken in my desktop software stack.  I do have a hint as to what it may be, as my system was broken by a misconfiguration...

I run a 12.04LTS desktop machine.  One of my colleagues recently attempted to apply his custom system backup/management system to the machine.  Unfortunately this system was tailored for redhat, and overwrote the /etc/{shadow,passwd,gshadow,group} files. In doing so, it broke entirely the desktop environment (relabeling all groups, so the desktop environment lost essentially all permissions, and couldn't launch).  It also broke many other essential system services (like networking).  I, fortunately, had a backup of all of these files, and restored them, although I'm unsure how recent this backup was.  Upon restoration of /etc/{group,shadow,gshadow,passwd} of my system services are running again, with the exception of the ability to unlock my screen.  I've briefly looked at my /var/log/syslog, and I've seen nothing indicating any form of an error.

One final note, if I attempt to disable the screen locking with `gsettings set org.gnome.desktop.screensaver lock-enabled false` after my screen has locked (through tty1) I get a dbus error (I'll update this post with it shortly, but I don't want to lock my system now, as I'm typing this email).  If I run this command before my screen is locked I get no dbus error.  I'm unsure if this is related (although it seems likely).

Thank you for any assistance you can give.

---

