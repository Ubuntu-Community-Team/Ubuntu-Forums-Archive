---
title: "gnome-shell broken with today update"
date: 2010-06-21
forum: Desktop Environments
---

### Post by giorsat on 2010-06-21
Hi everybody. Today I updated the gnome-shell package from ricotz ppa and it gave me a bunch of errors.
now I have the gnome-shell package broken and I'm not able to delete it nor with synaptic nor with apt-get purge 
it gives a glib compile schemas not foud exit error status 127

what can I do to get rid of this package and try reinstall? or is it a problem of the gnome-shell package itself?

---

### Post by yossell on 2010-06-21
Since it's from another ppa I wonder if this might help you at least remove it.

[http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html)

---

### Post by giorsat on 2010-06-21
thank you but I can't install a new deb package until this one is purged or installed properly

---

### Post by milky2313 on 2010-06-21
I got the same error. Looks like a problem in the most recent gnome-shell package. I found a temporary fix to at least remove the package:
```
sudo ln -s /bin/true /bin/glib-compile-schemas
```

Then you should be able to properly uninstall the gnome-shell package. When you are finished uninstalling, get rid of the link created by the above command:
```
sudo rm /bin/glib-compile-schemas
```

---

### Post by wojox on 2010-06-21
Build it and you won't have those problems. :p

---

### Post by urasmm01 on 2010-06-21
I had the same problem with ricotz packages. Seems like the dependencies are off. To get the missing dependency, glib-compile-schemas, install the libglib2.0-dev package.

```
sudo apt-get install libglib2.0-dev
```

Then install or remove gnome-shell.

```
sudo apt-get install gnome-shell
```
or
```
sudo apt-get remove gnome-shell
```

---

### Post by giorsat on 2010-06-22
thanks!!!

---

### Post by impresionist on 2010-06-29
> **urasmm01 said:**
> I had the same problem with ricotz packages. Seems like the dependencies are off. To get the missing dependency, glib-compile-schemas, install the libglib2.0-dev package.

```
sudo apt-get install libglib2.0-dev
```

Then install or remove gnome-shell.

```
sudo apt-get install gnome-shell
```
or
```
sudo apt-get remove gnome-shell
```

Hello,
I'm installing the Empathy 2.31 in my Lucid, and when I run the ./autogen.sh, I get configure: error: glib-compile-schemas not found

I compile the libglib2, and the nome-shell as you said, but no way, I still getting the same error...
Any help, please!
Thanks in advance,

---

### Post by Elktro on 2010-11-07
Same problem! I'm trying to compile evince-2.91.1, but configure gives:

 configure: error: glib-compile-schemas not found.

libglib2.0-dev I already have. and installing gnome shell didn't help.

---

### Post by doraimom on 2012-02-06
Hi.
I'm having the same problem with the package glib-compile-schemas, needed to install System Load Indicator.

My system is debian stable kernel 2.6.32-5-686.
I have installed all libglib packages listed in Synaptics.

I can't find neither the package libglib2.0-BIN (no libglib ended with BIN in the list of my repository) nor gnome-shell in my repository:
> deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) squeeze main contrib non-free

How can I solve this dependency problem with the package glib-compile-schemas?
Thank you

---

### Post by andisl on 2012-02-25
Thank you a lot!

This help me to get rid of Cinnamon, showing error message "E: cinnamon-extensions-extended-places-menu: subprocess installed post-removal script returned error exit status 127"

Andis

---

