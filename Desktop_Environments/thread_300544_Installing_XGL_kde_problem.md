---
title: "Installing XGL kde problem"
date: 2006-11-15
forum: Desktop Environments
---

### Post by SexyPastry on 2006-11-15
I keep getting this error when i was installing XGL ```
sudo apt-get install xserver-xgl

```

I keep getting this error ```
sudo apt-get install xserver-xgl
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.88.4-1ubuntu2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any ideas?

---

### Post by d3v1ant_0n3 on 2006-11-15
Looks like XGL installed fine, but clamav didn't- I'm guessing you've tried to install this before?

---

### Post by SexyPastry on 2006-11-15
yea how do i fix that?

---

