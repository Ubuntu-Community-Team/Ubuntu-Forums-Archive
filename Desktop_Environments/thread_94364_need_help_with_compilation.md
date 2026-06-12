---
title: "need help with compilation"
date: 2005-11-23
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-23
im trying to compilate a kernel for booting two boxes diskless 
i already download and install bootp. tftp, xinet and nfs im following a tutorial for it.

i also download the linux-source-2.6.12 but i cant configure it this message appears:

:/usr/src/linux-source-2.6.12$ make xconfig
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

any idea

10x in advanced

---

### Post by RAOF on 2005-11-23
Well, you need the gcc-3.4 packages.
```
sudo apt-get install build-essential gcc-3.4
```
should get you all that you need to build the kernel.  Additionally, running "make gconfig" rather than "make xconfig" will use a gnome configuration program, so you don't need the qt-libs.

---

### Post by mxyzptlk on 2005-11-23
all right thanks for answering but i think i have those packets, anyway ill download them again and ill post the results


thanks again

---

### Post by mxyzptlk on 2005-11-23
well now i have this one:

/usr/src/linux-source-2.6.12$ make gconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*
make[1]: *** [scripts/kconfig/.tmp_gtkcheck] Error 1
make: *** [gconfig] Error 2


 i think i need those ones two dont i?

---

### Post by RAOF on 2005-11-23
You'd be after the gtk2.0-dev, glib2.0-dev and glade-dev packages (I'm not sure if those are the exact names.  Use synaptic's search to find the real packages).  In any case, if it goes on to complain about needing foo, search in synaptic for the foo-dev package.

---

### Post by mxyzptlk on 2005-11-23
well they are no in synaptics.

is there any apt source to download them or should i do it by hand

---

### Post by RAOF on 2005-11-23
The packages you are after are **definitely** in synaptic.  The names I gave might not have been correct, though.  Search (by name only) for "gtk", "glade", and "glib", and there will be -dev versions of the packages.  Those are the ones you want.

Oh, and it's possible (but unlikely, I think) that they're in the Universe or Multiverse repository.  If you don't have those enabled, try enabling them.

---

### Post by mxyzptlk on 2005-11-24
well you were right i enabled the repos and there they are

hopefully my compilation wont have any more tricks

ill tell you the results

thanks again

---

### Post by mxyzptlk on 2005-11-25
the kernel is ready but the how to i am reading is mentioning something about that i have to tagged it with this command:

/sbin/mknbi-linux -d rom -i rom -k bzImage -o bootImage

and it says

/sbin/mknbi-linux no such a file or folder

mknbi is already installed


any idea

10x in advanced

---

### Post by ranf on 2005-11-25
[QUOTE=mxyzptlk]
/sbin/mknbi-linux no such a file or folder

mknbi is already installed
[/QUOTE]

`dpkg -L mknbi' lists all installed files. Most likely it is not installed in `/sbin' but somewhere else.

---

