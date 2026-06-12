---
title: "Compiling FF 1.07 from source"
date: 2006-01-12
forum: Desktop Environments
---

### Post by ashrack on 2006-01-12
When trying to compile FF 1.07 from source I get the following error when doing
'./configure'

```
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found.
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
*** GTK+ is available from ftp://ftp.gtk.org/pub/gtk
configure: error: Test for GTK failed.

```
What must I install to get this working?

---

### Post by kaamos on 2006-01-12
Try installing libgtk1.2-dev.

---

### Post by ashrack on 2006-01-14
[QUOTE=kaamos]Try installing libgtk1.2-dev.[/QUOTE]
Tanx how did U know which one to install?
/////////////////////
No I have another dependecy problem:
```
checking for libIDL-config... no
checking for libIDL - version >= 0.6.3... no
*** The libIDL-config script installed by libIDL could not be found
*** If libIDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBIDL_CONFIG environment variable to the
*** full path to libIDL-config.
checking for orbit-config... no
configure: error: libIDL not found.
        libIDL 0.6.3 or higher is required.

```
But I have 'libidl0,libidl-dev' installed. So what do I need now?

---

### Post by aysiu on 2006-01-14
Just out of curiosity, is there a reason you're installing from source instead of through apt-get?

---

### Post by ashrack on 2006-01-14
[QUOTE=aysiu]Just out of curiosity, is there a reason you're installing from source instead of through apt-get?[/QUOTE]
learning I guess and curiosity.

btw. did ```
sudo apt-get build-dep firefox
```
but I still get the same 'libidl' dependency problem

---

