---
title: "GDM+FluxBox autologin fails"
date: 2012-10-03
forum: Desktop Environments
---

### Post by StickyC on 2012-10-03
I'm trying to set up an Ubuntu 12.04 system (based on the Server install) with GDM and FluxBox to auto-login. Accord to what I've read, I just need to add the following to /etc/gdm/custom.conf (which is otherwise empty):
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=cweiss
```

However, when added, the system does not launch X11, but sits in text mode. When not present, I get the normal GDM greeter and Fluxbox is selected by default (it's the only windowing system install) and I can launch it just fine.

I must be missing some other directive, but I sure can't find anything obvious in the docs. Any ideas?

---

