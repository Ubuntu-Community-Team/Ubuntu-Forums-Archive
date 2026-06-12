---
title: "how do I know which gtk+-2.8.9 dependency is not met?"
date: 2006-01-06
forum: Desktop Environments
---

### Post by fealz on 2006-01-06
I've been having problems using ./configure with many programs because my version of glib was apparantly too old, so I attempted to update glib and I was told I needed to update gtk+ too, and to do that, I needed to update cairo, atk, and pango.  So, I downloaded atk-1.10.3, cairo-1.0.2, glib-2.9.1 and pango-1.11.1.  I thought I installed them all, but I must have done something wrong because when I try to install gtk+-2.8.9 after, I get this message:

> checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


anyone have a suggestion of what I should do to check the versions of everything that I have installed?  or to install them all correctly?

Thanks.

---

### Post by dsjas297 on 2006-01-06
It seems like you need a later version of atk. Note how the dependencies listed say you need atk 2.7.1 or later.

---

### Post by fealz on 2006-01-06
[QUOTE=dsjas297]It seems like you need a later version of atk. Note how the dependencies listed say you need atk 2.7.1 or later.[/QUOTE]


really?  I thought it was saying I needed atk 1.0.1 or later..  are you sure you're reading that right?  maybe it's me.. i'll look around, but anymore info would be great.  Thanks!

---

### Post by fealz on 2006-01-07
Also, I read that when installing glib, it will overwrite the old version if you type > ./configure --prefix=/usr

This seems to work, but would it work with pango, atk, gtk+ and cairo too?  if not, is there something else I should do to overwrite the old files?

---

### Post by Galoot on 2006-01-07
[QUOTE=dsjas297]It seems like you need a later version of atk. Note how the dependencies listed say you need atk 2.7.1 or later.[/QUOTE]That'd be a neat trick. [Atk is at 1.10.3]("http://developer.gnome.org/doc/API/").

'course, I always run into dependency issues and stuff when I'm time-traveling, so you never know. :)

---

### Post by dsjas297 on 2006-01-07
Sorry about that. Should have looked at the post more closely.

---

### Post by fealz on 2006-01-07
[QUOTE=Galoot]That'd be a neat trick. [Atk is at 1.10.3]("http://developer.gnome.org/doc/API/").

'course, I always run into dependency issues and stuff when I'm time-traveling, so you never know. :)[/QUOTE]

lololol, yea, that's what I thought!  thanks for confirming.

but no one knows how I can fix this?  Either to uninstall all of the dependencies and re-install, to check which versions I have installed, or to overwrite the old versions with the new ones?  any help would be greatly appreciated...

---

