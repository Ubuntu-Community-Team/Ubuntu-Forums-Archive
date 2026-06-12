---
title: "Trying to Compile pygtk....."
date: 2009-05-08
forum: General Help
---

### Post by toejamfootball on 2009-05-08
At ./configure I get this error.

checking for GLIB - version >= 2.8.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: gobject is required to build pygtk?

I try to get "gobject" and it says I already had it 

python-gobject is already the newest version.


I'm not sure what to do....

EDIT: OK, I got past that, now I get this error - 

checking for PYGOBJECT... configure: error: Package requirements (pygobject-2.0 >= 2.12.1) were not met:

No package 'pygobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGOBJECT_CFLAGS
and PYGOBJECT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by toejamfootball on 2009-05-08
OK well, I figured out I can get it from the repos.... but how do I run it? I can't find it anywhere.

Sorry, I meant to edit.

Does pygtk even have a front end GUI? Or is it just CLI?

---

