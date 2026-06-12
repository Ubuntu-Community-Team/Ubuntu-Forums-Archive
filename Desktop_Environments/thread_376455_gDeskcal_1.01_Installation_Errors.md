---
title: "gDeskcal 1.01 Installation Errors"
date: 2007-03-04
forum: Desktop Environments
---

### Post by Icarus3000 on 2007-03-04
I downloaded the latest version of gDeskcal from here:
[http://www.pycage.de/#gdeskcal]("http://www.pycage.de/#gdeskcal")

I followed the installation instructions by running ./configure, and get the following error:

```
checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.6.0) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Can someone advise me what to do next?

Thanks,
Icarus3000

---

### Post by raja on 2007-03-04
You can install python-gtk2 from the repositories with apt-get. Of course you can also install gdeskcal from the repository, but maybe you wanted the latest.

---

### Post by Icarus3000 on 2007-03-04
Thanks, but python-gtk2 is already installed.

And I do want the latest version of gdeskcal.

---

### Post by emid on 2007-03-14
> **Icarus3000 said:**
> Thanks, but python-gtk2 is already installed.

And I do want the latest version of gdeskcal.


I was having a similar issue while installing gimmie.  I resolved it by installing the dev package for python-gtk2.  I would give that a try.

The package would be python-gtk2-dev.

---

### Post by cendant on 2007-03-19
Congifure works, but Make fails. Can you help me find out why?


andrei@acer:~/Desktop/gDeskCal-1.01$ make
Making all in code
make[1]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/code'
Making all in planner
make[2]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/code/planner'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/code/planner'
make[2]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/code'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/code'
make[1]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/code'
Making all in data
make[1]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/data'
Making all in gfx
make[2]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/data/gfx'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/data/gfx'
make[2]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/data'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/data'
make[1]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/data'
Making all in ical
make[1]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/ical'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/ical'
Making all in po
make[1]: Entering directory `/home/andrei/Desktop/gDeskCal-1.01/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[1]: *** [ar.gmo] Error 127
make[1]: Leaving directory `/home/andrei/Desktop/gDeskCal-1.01/po'
make: *** [all-recursive] Error 1
andrei@acer:~/Desktop/gDeskCal-1.01$

---

