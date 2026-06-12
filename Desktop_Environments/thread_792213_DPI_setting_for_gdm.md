---
title: "DPI setting for gdm"
date: 2008-05-12
forum: Desktop Environments
---

### Post by ragespot on 2008-05-12
Hi!

Im with Ubuntu 8.04 and i'm having trouble to change the dpi setting.
I used a HD TV for the screen and since this,in the GDM and in other program like Amsn, the font is extreamely small. In 7.10 I out the -dpi 96 in the login windows/ security /X command   and it worked fine. but now with this option, it doesn't save. and I tried to force it in the gdm.conf file and it doesn't work.

I  add the -dpi 96 part int he gdm.conf like this:

```
# X Server Definitions
#
# Note: Is your X server not listening to TCP requests?  Refer to the 
# security/DisallowTCP setting!

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 96
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0
```

have an idea how I could change the dpi this time?

---

