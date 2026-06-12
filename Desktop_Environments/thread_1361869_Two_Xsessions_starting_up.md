---
title: "Two Xsessions starting up"
date: 2009-12-22
forum: Desktop Environments
---

### Post by storm_to on 2009-12-22
I uninstalled latest kdm and installed legacy v2.2 kdm so that I can make my login look like Apple MAC OSX etc....
 
Now there are two sessions starting
Default kdm on :0
Default gdm on :1
 
I disabled kdm daemon, even went as far as uninstalling it (wouldn't boot up until kdm was reinstalled). 
Something is still starting up two X sessions!?!?!?
 
 
Anyone know where I can go looking for the cause of dual start and disable the 1st one?
 
Thanks!

---

### Post by storm_to on 2009-12-23
Figured it out myself.
 
Noticed that gdm has **/etc/X11/default-display-manager **and gdm-2.20 removes it.
Both kdm and gdm check there to see if they are the default before starting up.
Since they can't find it, they both start up.
 
Soltution is:
```
sudo echo "/usr/sbin/gdm" > /etc/X11/default-display-manager
```

---

