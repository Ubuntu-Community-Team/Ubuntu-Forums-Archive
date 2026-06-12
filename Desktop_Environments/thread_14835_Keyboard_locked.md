---
title: "Keyboard locked"
date: 2005-02-10
forum: Desktop Environments
---

### Post by kamstrup on 2005-02-10
When I am logged in as my ordinary user, the keyboard is locked up. No matter what key I hit it just goes "beep" from the system bell. I am perfectly able to log in as this user through gdm. It is as soon as I am logged in, things go wrong.

When I am logged in as another user it is all ok. Also if I login in a pure terminal (no X), everything works fine. 

This all started while I was playing Enemy Territory. Suddenly for no apparent reason, the computer just went "beep" instead of accepting keyboard input.

PS: I have not upgraded anything lately.

---

### Post by kamstrup on 2005-02-10
Just tried the lemming thing: rebooting.

It did not help. I have a Slackware dualboot. The keyboard is also locked as this user when logged in from Slackware.

---

### Post by kamstrup on 2005-02-10
Somebody please help... I am becomming desperate.

I have tried clearing my /tmp and ~/tmp but to no avail. My .Xauthority had something that looked like garbage in it, so I deleted it. The other (working) accounts doesn't have any .Xauthority file so I guess I don't need one...

.xsession-errors says something like this:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mikkel"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/bitsplitter:/tmp/.ICE-unix/4347
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
looking for type: got text/plain
looking for type: got text/plain
looking for type: got text/plain
looking for type: got application/x-gnome-app-info
looking for type: got text/plain
looking for type: got text/plain
looking for type: got text/plain
Vindueshåndteringsadvarsel: Broken client! Window 0x2800002 (aterm) changed client leader window or SM client ID
umount: only root can unmount /dev/hda1 from /media/windows
umount: only root can unmount /dev/hda5 from /media/slackware
umount: only root can unmount /dev/hda7 from /
umount: only root can unmount /dev/hda8 from /media/space
umount: only root can unmount /dev/hda9 from /home

(nautilus:4455): Eel-CRITICAL **: file eel-preferences.c: line 872 (preferences_entry_remove_callback): assertion `entry->callback_list != NULL' failed

** (nautilus:4455): WARNING **: destroyed file still being monitored

** (nautilus:4455): WARNING **: destroyed file still being monitored

** (nautilus:4455): WARNING **: destroyed file still being monitored

** (nautilus:4455): WARNING **: destroyed file still being monitored
```

---

### Post by kamstrup on 2005-02-10
Just remembered the failsafe sessions.

If I try the failsafe xterm-session (no gnome), the keyboard works. If I try the failsafe gnome-session the keyboard does not work.

---

### Post by kamstrup on 2005-02-10
The plot is thickening...
-------------------------------------

I have been digging deeper into this. If I boot into X using a .xinitrc I am able start only metacity. Keyboard still works. I am also able start nautilus and gnome-panel and maintain a working keyboard.

It is as soon as I run gnome-session that my keyboard locks up.

During the gnome-session boot I hit my keyboard wildly to see the exact point where it fails; and that seems to be as the ubuntu splash-screen appears.


Please... Anyone?

---

### Post by rosslaird on 2005-02-10
It's really a bizarre problem.
I looked at the xsession-errors file, and everything in it looks reasonably common (the Nautlis errors are from crashing out of X, but are not an issue) except this:

> Vindueshåndteringsadvarsel: Broken client! Window 0x2800002 (aterm) changed client leader window or SM client ID
umount: only root can unmount /dev/hda1 from /media/windows
...etc.

That looks strange.

If it were me, I would remove the .gnome .gtk etc. files from the user's directory. In other words, I'd kill my gnome profile and start again. Depending on how much customizing you've done, this may or may not be an issue.

(The stuff in the .Xauthority file, by the way, is a cookie, and it alsways looks like garbage. I don't think that's your problem.)

Also look at the xorg file in /var/log (Xorg.0.log, I think). That is always very useful.

Good luck with this. It's a humdinger.

Ross

---

### Post by kamstrup on 2005-02-11
Thanks for the feedback.

I am afraid that "rm -rf .gnome*" is my only idea. I think I can spare gtk, since I have been able to succesfully run gtk-apps without locking the keyboard.

I fear that this problem will return, and I will have to nuke my gnome configs every now and then :-(

Suggestions are still accepted, can't delete anything before I get home.

---

### Post by kamstrup on 2005-02-11
Yeehaw! I fixed it!

The problem was somewhere in the GNOME accessibility features. Somehow something that shouldn't have been enabled, got enabled...

In case anybody else out there stumbles, here is my fix:

---------------------
1) In the graphical loginscreen click "Session" and choose the failsafe terminal session (ie. NOT GNOME failsafe), and log in.

2) Run the command "gconf-editor", and go to  "desktop->gnome->accessibility", and make sure none of the entries are marked with a check sign.

3) Close gconf-editor and log out (type "exit")

4) Choose the Gnome session from the graphical login screen, and log back in. Voila.

---

