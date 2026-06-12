---
title: "Error compling gDesklets 0.35.3"
date: 2006-01-31
forum: Desktop Environments
---

### Post by TeeAhr1 on 2006-01-31
I error out on the configure...
[I]checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
[/I]
Am I missing dependencies?  How can I tell?  Thx in advance...

---

### Post by TeeAhr1 on 2006-01-31
Okay, got through that one.  Download libxml-parser-perl from the repositories.  There are further dependencies listed in the gDesklets readme file.  However, I think I have them all, but I am now coming up with...
> checking for GDESKLETS... configure: error: Package requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GDESKLETS_CFLAGS and GDESKLETS_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

I am at a loss.  Anyone recognize this?

---

