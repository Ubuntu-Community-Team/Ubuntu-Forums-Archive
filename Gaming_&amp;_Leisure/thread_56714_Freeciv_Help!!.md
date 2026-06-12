---
title: "Freeciv Help!!"
date: 2005-08-13
forum: Gaming &amp; Leisure
---

### Post by warptrosse on 2005-08-13
Hi, i want to install Freeciv 2.0.4. When i execute ./configure it shows the following error to me:

```
checking for GTK+ - version >= 2.2.1... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for gtk-config... no
checking for gtk12-config... no
checking for gtk13-config... no
checking for GTK - version >= 1.2.5... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
```


i try to install GTK+, when i execute ./configure (GTK+) it shows the following error to me:

```
checking for glib-2.0 >= 2.0.6 atk >= 1.0.1 pango >= 1.0.1... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

configure: error: Library requirements (glib-2.0 >= 2.0.6 atk >= 1.0.1 pango >= 1.0.1) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

but, i have this three libs, i find him in synaptic:

>> libglib2.0-0 (installed version 2.6.3-1)
>> libglib2.0-0 (installed version 1.9.1-0ubuntu1)
>> libpango1.0-0 (1.8.1-0ubuntu2)

when i see this, i find "glib-2.0" in my disc -> locate glib-2.0 and it shows me:

```
/usr/lib/libglib-2.0.so.0.600.3
/usr/lib/libglib-2.0.so.0
```

i execute PKG_CONFIG_PATH='/usr/lib/libglib-2.0.so.0'

and i try ./configure again, but it shows the previous error to me...

i reinstall libglib2.0-0, libglib2.0-0 and libpango1.0-0.... and i try ./configure again, but it shows the previous error to me...


please help me...

thanks for all

---

