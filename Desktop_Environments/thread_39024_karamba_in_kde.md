---
title: "karamba in kde"
date: 2005-06-03
forum: Desktop Environments
---

### Post by thagame on 2005-06-03
i grabbed karamba from the main site and i run ./configure but i get this error 

checking for libXext... yes
checking for Xinerama... no
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

anyone else getting this error. and do i have to grab qt off the website cause i have almost everything in synaptic for qt3.

---

### Post by ltmon on 2005-06-03
It looks like the devel libraries from qt.

Try

libqt3-headers
libqt3-dev
libqt3-mt-dev

And see if it works then.

Also, is there any reason you can't just use the superkaramba in the repositories?

---

### Post by thagame on 2005-06-03
wont let me have libqt3-dev and dev-mt installed at same time. and i didnt know there was superkaramba in reposit as i never use synaptic except to see if something is installed.

---

### Post by Seth on 2005-06-03
[QUOTE=thagame]wont let me have libqt3-dev and dev-mt installed at same time. and i didnt know there was superkaramba in reposit as i never use synaptic except to see if something is installed.[/QUOTE]
 Good job on completely obviating the purpose of apt... :-/

---

### Post by thagame on 2005-06-03
so wheres my cookie smartass. this issue proved why i dont use it. superkaramba is old in repos and i had to get a newer version elsewhere.

---

