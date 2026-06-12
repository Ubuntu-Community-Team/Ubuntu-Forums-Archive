---
title: "Help with Nuvola theme / gtk-engine-2 problem"
date: 2005-07-13
forum: Desktop Environments
---

### Post by mpc823_99 on 2005-07-13
After much frustration (and extra installs of needed prereq's) in trying to install what I thought would be a simple Nuvola theme to my desktop, I have run into a problem I don't know how to fix. Though hopefully it is easy. I am trying to run 

```
./configure --prefix=/usr --enable-animation
```, but receive the error

```
checking for gtk-engines-2 >= 2.6.0... Package gtk-engines-2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-engines-2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-engines-2' found
configure: error: gtk-engines-2 is required to compile gnome-themes-extras
```

I have no idea how to fix this. Can anyone give me guidance on what to try to do next?

Thanks,
Daniel

---

### Post by Majlo on 2005-07-14
Hi..

Nuvola is in gnome-themes-extras .

Simply type

sudo apt-get install gnome-themes-extras

---

### Post by mpc823_99 on 2005-07-14
Well, that worked! Thanks. I looked through the message boards all night and never saw that simple apt-get.

---

