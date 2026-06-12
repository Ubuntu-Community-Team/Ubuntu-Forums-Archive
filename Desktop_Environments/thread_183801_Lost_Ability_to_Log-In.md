---
title: "Lost Ability to Log-In"
date: 2006-05-28
forum: Desktop Environments
---

### Post by jwh400 on 2006-05-28
While using gFTP to transfer some photos to my website I changed the chmod of a pic on my desktop from the gFTP interface. When I did this the desktop wallpaper disappeared so I closed gFTP and tried to restart it but it wouldn't. I did a restart of the computer but after logging in I was prompted that the session lasted less than 10 seconds and to try to use a failsafe method of logging in. Using failsafe I got;

"/etc/gdm/preSession/Default: Registering your sesion with wtmp and utmp
/etc/gdm/Presession Default: running : /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " ' -1 ' :0" 'jeffrey'

(gnome-session: 8167): libgnome-WARNING ** Unable to create ~/.gnome2 directory: Permissin denied
Could not create per-user gnome configuration directory '/home/jeffrey/.gnome2 / ' : Permission denied 

I tried the failsafe terminal method using gksudo nautilus and I got;

bash:/ /home/jeffrey/bashrc: Permission denied
jeffrey@CyberPOWER:~

After typing gksudo nautilus i got;

**(gksudo:8240):WARNING ** Lock taken by pid: -1. Exiting

I'm sure it has something to do with changing the chmodding on the pic that was on the desktop but I can't figure out how to get to it to either change it back or delete it. I've been running Breezey Badger for several months and this is my first catastrophe. :-D ](*,) 
:D

---

### Post by jwh400 on 2006-05-28
I was able to set myself up with a root password so I could log-in and was able to get to the desktop. I still don't know what happened to my user account but I'll create another and move my files to it. Hopefully that will work.
:D

---

