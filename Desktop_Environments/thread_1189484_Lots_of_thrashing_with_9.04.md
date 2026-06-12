---
title: "Lots of thrashing with 9.04"
date: 2009-06-16
forum: Desktop Environments
---

### Post by wincen on 2009-06-16
kjournald2 is almost always running and I don't know why.

I'm using Jaunty 9.04 x64 and it's generally been pretty nice except for the tons of thrashing I get with my desktop.

Any ideas why?  I really don't know which process would cause this.

---

### Post by wincen on 2009-06-17
ok after installing iotop i saw that the problem seems to be coming from syslogd.  it's constant running and constantly writing...

syslogd provides support for system logging and kernel message trapping... i killed it for now, but perhaps there is a better setting out there to prevent it from constantly writing?

---

### Post by wincen on 2009-06-17
well talking to myself here, but maybe this will help someone out there that runs into the same problem as myself.

i found what was causing the constant logging.  mythtv and nullmailer.  I just uninstalled mythtv.  as for nullmailer, it wasn't properly configured in /etc/nullmailer/remotes.  Once I put in some values it stopped the constant logging every 5 seconds.

thrashing is no more.  yay.

---

