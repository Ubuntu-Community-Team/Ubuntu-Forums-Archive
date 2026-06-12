---
title: "Difficulty Logging into Gnome"
date: 2007-04-23
forum: Desktop Environments
---

### Post by rudeboyskunk on 2007-04-23
Ok, this only started happening today.  Every time I log into Gnome, during all my initial startup programs, it will just log itself back out.  Then when I log back in, it loads everything, but I get the "you were only logged in so long..." window, and if I click "OK" on that, I get logged back out.  So I don't click OK, and I can do almost everything (a few things won't work, like gnome-session-properties).  Here is the error log:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rudeboyskunk"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/skamasterflex:/tmp/.ICE-unix/5535

(evolution-alarm-notify:5627): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:5621): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

I'm running a HP 751n, 1.8 GHz, Pentium4, Feisty Fawn.

I really don't want to have to do a clean install...

EDIT:
When I go to a terminal and try to go to gnome-session-properties, I get this error message:

rudeboyskunk@skamasterflex:~$ gnome-session-properties

(gnome-session-properties:6020): GnomeUI-WARNING **: While connecting to session manager:
Could not open network socket.
could not connect to the session manager

---

### Post by rudeboyskunk on 2007-04-23
Ok, I figured out the problem.  I'm not sure why it's a problem, but I fixed it.  I put beryl into my sessions so that it would start up immediately upon logging in.  Because I couldn't get into gnome-session-properties, I had to go into synaptic and remove all my beryl files.  Anybody else have this problem, or know why this happens?

---

### Post by beerorkid on 2007-04-23
I remember back a few distros, hoary maybe?   I had this problem a bunch.  Had to do with the /home/username/.ICEauthority file.  Changing the permissions to user or deleting it fixed the problem.

I too have been there with issues and having to uninstall beryl to get back logged in.  Still it is nice to have beryl start up right away.

---

