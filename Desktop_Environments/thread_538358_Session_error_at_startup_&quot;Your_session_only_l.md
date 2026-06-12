---
title: "Session error at startup &quot;Your session only lasted less than 10 seconds&quot;"
date: 2007-08-29
forum: Desktop Environments
---

### Post by freakanth on 2007-08-29
Hi,

Whenever I login, I get an error message that says the following

"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem."

Disk space is not a problem for sure. I have enough space left on all my drives.

The error log in the .xsession-errors file says

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "srikanth"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/RustyCage:/tmp/.ICE-unix/5384
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension

(evolution-alarm-notify:5475): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

I looked this problem up on quite a few forums. These are the things I tried but didn't work

1. Change permissions of/delete ~/.ICEauthority
2. Change permissions of/delete ~/.Xauthority
3. Move ~/.gnome and ~/.gnome2 to /tmp (I don't know how this could have helped though)
4. Reinstall "gnome-session"

Is there any other way of fixing this problem. The last time it happened, it got corrected when I deleted ~/.ICEauthority.

Srikanth

---

### Post by picpak on 2007-08-29
Your session ONLY lasted less than 10 seconds? What, you want it to do worse? :lolflag:

Seriously though, the last time this happened to me it was because I deleted /tmp (or the contents of it). For the record, you *really* need this folder. Did you do that?

---

### Post by freakanth on 2007-08-30
No i didn't do anything to the /tmp folder. I had just installed Enlightenment desktop on my system and wanted to check it out. So I did a Ctrl+Alt+Backspace to restart X. The problem started then.

Oh and I still have read/write permissions to .ICEauthority and .Xauthority files.

srikanth@RustyCage:~$ ls -al

-rw-------  1 srikanth srikanth    495 2007-08-30 14:54 .ICEauthority
-rw-------  1 srikanth srikanth    120 2007-08-30 14:54 .Xauthority

---

