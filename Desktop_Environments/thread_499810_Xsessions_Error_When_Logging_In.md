---
title: "Xsessions Error When Logging In"
date: 2007-07-13
forum: Desktop Environments
---

### Post by malanis1 on 2007-07-13
Im getting an error that says:
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Im using ubuntu feisty fawn, the most recent.

My .Xsession-error file:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "malanis"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: libgconf-2.so.4: cannot open shared object file: No such file or directory

What is libgconf-2.so.4?  Any ideas why this happened?  any help would be appreciated... thanks.

---

### Post by aquavitae on 2007-07-13
libgconf is one of the base libraries for gnome.  If its missing you've probably got a problem with the gnome installation.  Try reinstalling it using the command apt-get install libgconf2-4

---

### Post by malanis1 on 2007-07-15
I tried doing that, didn't work... i was reading through the forum and I decided to reinstall ubuntu-desktop, and gdm... when i try to login again, i get the same error message... any help?

---

### Post by aquavitae on 2007-07-16
Is the file actually there - check /usr/lib or /usr/share/lib for it.  Or try the command "locate libgconf"

---

### Post by malanis1 on 2007-07-18
yeah it's in \usr\lib ... its contents are gconfd-2 and gconf-sanity-check-2 and another folder called "2".. in it are 3 libgconfbackend files... one for evoldap, one for oldxml and one for xml...

---

