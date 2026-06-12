---
title: "X wont start anymore for regular users"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jinx099 on 2006-06-03
I get this error message when I login (with the GUI login screen) with the regular user:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ryan"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
```

I CAN login fine with the rot account.  I made a brand new account also and it does the same thing as my original account.  Any help will be appreciated!

---

### Post by Mustard on 2006-06-03
Seems strange, as normally the root account is disabled from logging into X via gdm.  The way you have it seems to be the reverse of what the default setup is.  What changes have you made recently that would have brought this about?

---

### Post by jinx099 on 2006-06-03
[QUOTE=Mustard]Seems strange, as normally the root account is disabled from logging into X via gdm.  The way you have it seems to be the reverse of what the default setup is.  What changes have you made recently that would have brought this about?[/QUOTE]
I shoud specify how I login to X with root.  I can either just type startx when booting in the recovery session, or I can sudo startx from my regular user.

It seemed to happen right after I commented out the line "Load dri" in the xorg conf file, but of course I set it back...

---

### Post by jinx099 on 2006-06-04
I should note that this is an AMD64 install, maybe I shoul reinstall it with the plain old i386 version, but I would like to get this figured out.

---

### Post by Mustard on 2006-06-04
Did you do a server install or something, and then build up from there?  I'm just curious why you need to type in startx to start the xserver.  Normally Ubuntu would install gdm for handling the login.  With regards to the error message I'm really not sure whats going on there.

---

### Post by Waywocket on 2006-06-04
What happens if you run startx from a terminal as a normal user?

In any case, you might want to check the permissions on your /tmp directory, in case it's become writable only to root.

---

### Post by jinx099 on 2006-06-05
[QUOTE=Mustard]Did you do a server install or something, and then build up from there?  I'm just curious why you need to type in startx to start the xserver.  Normally Ubuntu would install gdm for handling the login.  With regards to the error message I'm really not sure whats going on there.[/QUOTE]
I did a regular AMD64 install from the DVD.  When I boot normally, yes, it goes to the GDM screen and I am screwed.  However, if I boot the recovery kernel it boots to a command line as root where I can startx as root.  Or I can log in to my normal user and then startx where I get the same error.

I cant see how the /tmp permissions could have been changed, but I will check it out.

---

