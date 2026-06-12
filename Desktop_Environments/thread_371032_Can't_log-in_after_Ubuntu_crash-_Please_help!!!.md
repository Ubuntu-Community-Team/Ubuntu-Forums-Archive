---
title: "Can't log-in after Ubuntu crash- Please help!!!"
date: 2007-02-26
forum: Desktop Environments
---

### Post by navneeth on 2007-02-26
I was just changing icon themes, when all of a sudden the icons on the desktop and the panel disappeared.(I've been noticing that using the Themes Manager makes the Processes applet go all blue) I was still able to access the windows, but nothing much else. (It was a semi-crash, so to speak) So I rebooted the computer, but it would not go beyond the splash. I rebooted again, and entered the graphical failsafe mode, and that's where I'm typing this message from.  

As soon as I logged, an error message popped up

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

I'm not sure what to do to get back to my original desktop. Please help.

---

### Post by navneeth on 2007-02-26
It's been an hour and no one has read this thread but me???

Please help. I see a lot of other people having similar problems. In some cases, they seemed to have solved it by fiddling with gnome files, but I don't understand any of it.

---

### Post by SigmundFreud on 2007-02-26
I did some Googling. Apparently you need to re-install the dbus packages. I think it's something like apt-get install dbus   .

---

### Post by Wicca on 2007-02-26
I have this problem often, since upgrading to Edgy some icons seem to be corrupted.
In graphical failsafe mode just change your iconset and reboot. And never use that iconset again.

The message about dbus is because you're in safe mode (where it is not initialized i think) so not really a problem.

---

