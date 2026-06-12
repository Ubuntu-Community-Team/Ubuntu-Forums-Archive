---
title: "GNOME Startup Error"
date: 2006-06-20
forum: Desktop Environments
---

### Post by AngryKidJoe on 2006-06-20
First off, I'd like to say that I'm posting here because the GNOME user forums will not allow a new user to register. There's a bug in their forums at the moment. I'll try later. 
------------
I did a warm boot on Ubuntu 6.06 because my DVD drives weren't reading the DVDs during copying files anymore *(installing DooM 3)*. The files were showing up as "?????". Upon the login screen I got this error: *(They could be a bit off as I copied them by hand, I'll double check)*
```
**(~/.xsession-errors file)**
/etc/gdm/presession/default: registering your session with wtmp and utmp
/etc/gdm/presession/:default: running: /usr/bin/sessreg -a -w /var/log/utmp -x "var/lib/gdm/:0 xservers" -h "" -l ":0" "user"
etc/gdm/xsession: beginning session setup...
mkdtemp: private socket dir: permission denied
```

I decided to give the GNOME Failsafe a try and then I got this error:
```
Please contact your system administraator to resolve the problem: 
Could not open or create the file "(null)": This indicates that there may
be a problem with your config, as many programs will need to create files
 in your home directory.

The error was "Failed to create file 'tmp/gconf-test-locking-file-026eww": 
Permission Denied" (errno=2)
```

---

### Post by qhaz on 2007-01-31
Hi, I am getting the same error message at the moment as you when trying to start with GNOME Failsafe.  I wonder if you could share how you managed to correct this problem?

---

