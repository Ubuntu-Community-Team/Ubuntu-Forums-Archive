---
title: "Compilin missing some dev files"
date: 2006-10-03
forum: Desktop Environments
---

### Post by christooss on 2006-10-03
First app that Im compiling when ./configure throws out this error

> checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.7 gstreamer-base-0.10 >= 0.10.7) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GST_CFLAGS and GST_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

Which dev files do I have to install. Im using Dapper and apt-cache show gstreamer say that version of gstreamer is 0.10.7

Second app throws out this Error
> checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
configure: error: Cannot find GL library


Thanks for the anwsers

---

### Post by Shimmy on 2006-10-03
I think you need to install the dev packages.. for example "libgstreamer0.10-dev" for your first app.

---

### Post by Rui Pais on 2006-10-03
hi,
try to install libgstreamer0.10-dev and/or libgstreamer-plugins-base0.10-dev

maybe that works

---

### Post by christooss on 2006-10-03
The packages you mentioned are already installed :(

---

### Post by Shimmy on 2006-10-03
are you sure they are the dev-packages?
And i'm not sure, but you might need the correct version of the dev-packs, if you have gstreamer0.10.7 installed you might need the 0.10.7-dev package.

---

