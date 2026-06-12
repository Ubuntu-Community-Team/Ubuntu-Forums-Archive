---
title: "wavbreaker-0.7 problems with cinfigure"
date: 2006-03-06
forum: Desktop Environments
---

### Post by pbibb1657 on 2006-03-06
Hello
 Im having trouble getting wavbreaker-0.7 to configure on Ubuntu-5.10. I'm pretty  sure I have the files needed to configure this cool program. I have pasted the end of the configure script:

checking for WAVBREAKER... configure: error: Package requirements (gtk+-2.0 gthread-2.0 libxml-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the WAVBREAKER_CFLAGS and WAVBREAKER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


 If anyone has a few words of advice thanks

                                     Phillip:mrgreen:

---

### Post by Ampersand on 2006-03-07
You need to get the development packages for each of those libraries. Using Synaptic, install libgtk2-dev, libgthread2-dev and libxml2-dev (package names may vary, but they should be similar).

---

### Post by pbibb1657 on 2006-03-09
wow thanks I installled the programs you mentioned and viola! success sweet wavbreaker success

---

