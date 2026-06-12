---
title: "configure can't find mono"
date: 2006-08-19
forum: Desktop Environments
---

### Post by janhenderson on 2006-08-19
I get the following error when I try to configure csboard 


checking for MONO... configure: error: Package requirements (mono >= 1.1.0
) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I already installed mono libmono-1.1.13.6 mono-common mono-devel from the repositoreies but it's still not working. 

Any ideas?

---

### Post by croak77 on 2006-08-20
Make sure you have pkg-config and libmono-dev.

---

