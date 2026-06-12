---
title: "What does this mean? How do I update it? Please read."
date: 2009-05-21
forum: General Help
---

### Post by gymophett on 2009-05-21
```
checking for WNCK... configure: error: Package requirements (libwnck-1.0) were not met:

No package 'libwnck-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables WNCK_CFLAGS
and WNCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I can't install an app because of this. Can you explain what I need to do? Thanks. :)

---

### Post by taurus on 2009-05-21
It means that whatever you're trying to build is looking for libwnck.  So, go into synaptic and install libwnck & probably libwnck-dev before you build that program again.

---

### Post by gymophett on 2009-05-21
I did..
then I got this.. how to I update gtk?

```

Requested 'gtk+-2.0 >= 2.14' but version of GTK+ is 2.12.9

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables notify_osd_CFLAGS
and notify_osd_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by oldos2er on 2009-05-21
What program are you trying to compile?

---

