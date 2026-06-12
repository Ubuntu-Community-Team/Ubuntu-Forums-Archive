---
title: "Help! Have I completely hosed my system by unchecking a box?"
date: 2009-06-03
forum: General Help
---

### Post by brianary on 2009-06-03
So I put an SD card into the slot, and nothing happened. I could reboot, but I'd rather not. I thought I'd try restarting the dbus service, but I didn't have the keyboard nearby, so I opened the Services Settings window and unchecked System communication bus (dbus), thinking I'd just re-check it, and see if that would work.

The box wouldn't let me re-check it.

I rebooted, but after the reboot, I got the error "Unable to initialize dbus", and no input devices worked anymore. I switched to another terminal with Alt+F3 and restarted the dbus service, but when I opened the Services Settings window this time, the Unlock button was greyed out.

I found a thread that mentioned how to edit the PolicyKit.conf file to allow me to use the Services Settings window again, and I checked dbus and rebooted.

Now, following every boot, the message is "Unable to initialize hal", and the input devices still don't work unless I switch to another terminal and restart dbus, but the system is unstable, has no network, and seems to freeze on video playback (a problem for a MythTV box). During the boot process, there is also an avahi error.

I've tried using dpkg-reconfigure on dbus, hal, avahi, and network-manager, but nothing has fixed the problem.

Has that one checkbox totally hosed my system?

---

### Post by nickbooker on 2009-06-03
No it's not hosed, we just need to re-enable the missing services.

Try this...

In the terminal (Alt+F3), run:
 sudo update-rc.d dbus defaults
 sudo update-rc.d hal defaults

Then reboot.

---

### Post by brianary on 2009-06-03
Thanks for your quick reply! I will try that as soon as I get home, and let you know how it works.

---

### Post by brianary on 2009-06-03
I ran those commands, and got:

  System startup links for /etc/init.d/dbus already exist.
  System startup links for /etc/init.d/hal already exist.

Then, after checking the man page for update-rc.d, I tried:

  sudo update-rc.d -f dbus remove
  sudo update-rc.d -f hal remove
  sudo update-rc.d dbus defaults
  sudo update-rc.d hal defaults

And that fixed it! 

**MANY** thanks for your help!

---

