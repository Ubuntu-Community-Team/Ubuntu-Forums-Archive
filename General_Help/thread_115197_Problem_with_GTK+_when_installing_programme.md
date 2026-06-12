---
title: "Problem with GTK+ when installing programme"
date: 2006-01-10
forum: General Help
---

### Post by trfsonic on 2006-01-10
I am a newbie to Ubuntu.Ubuntu is great!:D 

When i am ./configure the PCMan(a telnet client, [Link]("http://sourceforge.net/projects/pcmanx/")), i encounter the following error

checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.

Cannot find GTK+/X11 2.4 (or above version)!

Can anyone help me to fix it?

---

### Post by Perfect Storm on 2006-01-10
```
sudo apt-get install build-essential
```

---

### Post by trfsonic on 2006-01-10
It won't work
The same message comes up again

---

### Post by lamego on 2006-01-10
You need to install gtk+ development libs.
Go to Synaptic and search for libgtk ...

---

