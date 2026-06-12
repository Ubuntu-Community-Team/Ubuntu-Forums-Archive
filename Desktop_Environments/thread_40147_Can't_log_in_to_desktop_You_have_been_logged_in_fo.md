---
title: "Can't log in to desktop: You have been logged in for less than 10 seconds"
date: 2005-06-07
forum: Desktop Environments
---

### Post by rivaitan on 2005-06-07
Hi guys. I've set up a little file and print server with ubuntu for a couple of days now. This morning I came in and tried to add a new printer, but I could bring up the "Add Printers" console. So, I restarted ubuntu. I haven't been able to log in to the desktop , it says something like "You have been logged on for less than 10 seconds ... and that there may be a problem with my installation or I'm running out of diskspace". I don't understand, Ubuntu installed fine. And yesterday, I had over 10GB of diskspace. Can someone help? I can't log in as administrator.  ](*,)

---

### Post by bored2k on 2005-06-07
Does it say something about "Ice" ?
BTW, if you need anything urgent, hit ctrl alt f1 and login in a bash prompt.

---

### Post by rivaitan on 2005-06-07
[QUOTE=bored2k]Does it say something about "Ice" ?
BTW, if you need anything urgent, hit ctrl alt f1 and login in a bash prompt.[/QUOTE]
 Not really ... here's the entire error message

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problme or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem

View details (~./xsession-errors file)"

Yep, thats it. I get this error message with all sessions except for failsafe xterm. So I think its a GNOME problem. Thanks for the tip on bash. The server is still up ... printing and sharing is still alright coz I managed to activate samba regardless. But I'd like my desktop back if possible. Hee hee. Thanks fellas.

---

### Post by KLineD on 2005-06-07
Press the view details button and post the error message.

---

### Post by rivaitan on 2005-06-07
[QUOTE=KLineD]Press the view details button and post the error message.[/QUOTE]
 /etc/gdm/PreSession/Default: Registering your session
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:0.Xservers" -h "" -l ":0" "oriental"
/etc/gdm/Xsession: Beginning session setup

(x-session-manager:7151): Gdk-WARNING **: locale not supported by Xlib
(x-session-manager:7151): Gdk-WARNING **: cannot set locale modifiers
Could not set mode 0700 on private per-user gnome configuration directory '/home/oriental/.gnome2_private/': Operation not permitted

Thats it
oriental is my user name

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=rivaitan]/etc/gdm/PreSession/Default: Registering your session
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:0.Xservers" -h "" -l ":0" "oriental"
/etc/gdm/Xsession: Beginning session setup

(x-session-manager:7151): Gdk-WARNING **: locale not supported by Xlib
(x-session-manager:7151): Gdk-WARNING **: cannot set locale modifiers
Could not set mode 0700 on private per-user gnome configuration directory '/home/oriental/.gnome2_private/': Operation not permitted

Thats it
oriental is my user name[/QUOTE]
 Does directory /home/oriental/.gnome2_private/ exist? What are permisssions and ownership of it (and of /home/oriental/) ?

---

