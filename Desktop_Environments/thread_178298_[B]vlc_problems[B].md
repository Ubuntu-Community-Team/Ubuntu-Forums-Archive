---
title: "[B]vlc problems[/B]"
date: 2006-05-17
forum: Desktop Environments
---

### Post by nikolaos on 2006-05-17
I tried to install atk because it is part of the process of installing gtk+ =>
=>which is part of the process of installing wxWidgets =>
=>which is part of the process  of installing vlc.](*,) 
If you are confused (i am), the thing that i need is what do i have to do about this error:
```
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```

again: it appears on atk configuration.

---

### Post by depu on 2006-05-17
have u tried using synaptic for installing vlc? it finds all the dependencies required on it own so that u dont have to hunt around for the packages.
anyways for the GLib error u have to install libglib2.0-0
i wud recommend that u try the synaptic first tho

---

### Post by nikolaos on 2006-05-17
i don't see anything in synaptics, no vlc package to install. And even glib seems to be installed but the problem remains.

---

### Post by depu on 2006-05-18
u need to have the universe and multiverse packages enabled in Synaptic to be able to see vlc there i think

---

### Post by nikolaos on 2006-05-18
thank you guys, i had to do is update the package list with the multiverse and universe packages in.
I just have one final question:
not xine 
neither vlc or totem can play .wmv files, is there a way to play those files in linux?

Thanks again.

---

### Post by depu on 2006-05-19
have a look at 
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

