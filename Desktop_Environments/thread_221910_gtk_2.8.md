---
title: "gtk 2.8"
date: 2006-07-24
forum: Desktop Environments
---

### Post by LORD_PoLvO on 2006-07-24
hi all does anyone know where i can downlaod the gtk2.8 so i can use good themes for my ubuntu as i couldnt get from the gtk website becasue all i got was a 0 kb word file lol

---

### Post by halfvolle melk on 2006-07-24
Hmm
```
wget ftp://ftp.gtk.org/pub/gtk/v2.8/gtk+-2.8.0.tar.bz2
```
does the trick over here.

---

### Post by LORD_PoLvO on 2006-07-24
hey thnx mate ill try that now

---

### Post by LORD_PoLvO on 2006-07-24
ahhh need help agai nim stuck compiling the file plz help 

```
 
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for strerror in -lcposix... no
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES_CFLAGS...
checking for BASE_DEPENDENCIES_LIBS...
configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
daniel@daniel-desktop:~/Desktop/gtk+-2.8.0$ make
make: *** No targets specified and no makefile found.  Stop.
daniel@daniel-desktop:~/Desktop/gtk+-2.8.0$

```

---

### Post by chavo on 2006-07-24
Uhm, Ubuntu comes with gtk 2.8.18. You can't have gnome without it.

---

### Post by LORD_PoLvO on 2006-07-25
then how come when i try to compile a gtk engine for a theme it says i need gtk 2.8??

---

### Post by cucisan on 2006-07-25
for compiling in general: if it says it needs package xxxx try installing package xxxx-dev :)

---

