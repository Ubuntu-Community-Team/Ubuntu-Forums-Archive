---
title: "GDAM installation problems"
date: 2005-12-20
forum: Desktop Environments
---

### Post by willhurt on 2005-12-20
Hi im trying to install GDAM from:

[http://gdam.sourceforge.net/](http://gdam.sourceforge.net/)

It looks like a really useful program. After viewing a couple of treads on this forum i tried installing the seperate .debs but got errors as xlib6 is now called xlibs, gdam was having none of it....

So im went for the tarball ./configure, make, make install.
But i cant get past the make stage i kept getting errors:

dasspatialstereo.c:73:40: pasting "->" and "lear" does not give a valid preprocessing token

After a bit of searching i came across this thread:
[http://www.mail-archive.com/cooker@linux-mandrake.com/msg126873.html](http://www.mail-archive.com/cooker@linux-mandrake.com/msg126873.html)

Which tells me to change a part of the file wihch ive done, now make gets past the dasspatialstereo section but i get the errors:

gcc -DHAVE_CONFIG_H -I. -I. -I../../common -I/home/will/downloads/gdam-0.942/include -DPREFIX_TOKEN=/usr/local -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -D_REENTRANT -I/usr/X11R6/include -I/usr/include/gnome-xml -I/usr/include/libglade-1.0 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gnome-xml -DGDAM_VERSION=\"0.942\" -O2 -c  -fPIC -DPIC gdamusbhid.c -o .libs/gdamusbhid.lo
gdamusbhid.c: In function 'translate_usb_input_to_name':
gdamusbhid.c:55: error: 'EV_RST' undeclared (first use in this function)
gdamusbhid.c:55: error: (Each undeclared identifier is reported only once
gdamusbhid.c:55: error: for each function it appears in.)
make[2]: *** [gdamusbhid.lo] Error 1
make[2]: Leaving directory `/home/will/downloads/gdam-0.942/component/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/will/downloads/gdam-0.942/component'
make: *** [all-recursive] Error 1


has anyone successfully got this working on breezy, i have all the dependancies installed but im new to linux, any help would be really appreciated, cheers will

---

### Post by err0r_ on 2006-07-12
I am having the same exact problem, wondering if you had found any answers to this.   Thanks, Will

---

### Post by billd42 on 2007-07-07
I'm having the exact same problems and it's nearly a year later.  :(

---

### Post by CodingQA on 2008-01-29
Ok to fix the issues ....

For dependency issues ...

sudo apt-get install libgtk2.0-0
sudo apt-get install libgtk2.0-dev
sudo apt-get install libgtk1.2-dev
apt-get install libglade2-0 libglade2-dev libglade0-dev libglade0 glade


Assuming the folder that you unzipped the files into is ~/gdam-0.942

You need to modify ~/gdam-0.942/server/plugins/gdasspatialstereo.c and change all references to ##prefix## to prefix##

Then go into ~/gdam-0.942/component/plugins/gdamusbhid.c

In the function translate_usb_input_to_name on line 53 change 

  if (evt->type  == EV_RST)
    return g_strdup_printf ("c:%d v:%d rst", evt->code, evt->value);

to

#ifdef EV_RST

  if (evt->type  == EV_RST)
    return g_strdup_printf ("c:%d v:%d rst", evt->code, evt->value);

#endif

then you should be able to configure and make the files

---

### Post by polmir on 2008-01-29
```
sudo apt-get install build-essential
```

---

### Post by pattone on 2008-03-22
Hello, I'm from argentine and my english is not the best.

I have done all that codingqa says adnd still can't make the install. I'm on ubuntu gutsy 7.10 and when I type make, after a long process came this errors:

pattone@pattone-desktop:~/gdam-0.942$ make
Making all in build
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/build'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/pattone/gdam-0.942/build'
Making all in doc
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/doc'
Making all in website
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/doc/website'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/doc/website'
Making all in jpegs
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/doc/jpegs'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/doc/jpegs'
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/doc'
./convert-sgml ./gdam.sgml txt:gdam.txt
./convert-sgml: 429: sgmltools: not found
./convert-sgml: error converting to text.
make[2]: [gdam.txt] Error 1 (no tiene efecto)
./convert-sgml ./gdam-dev.sgml txt:gdam-dev.txt
./convert-sgml: 429: sgmltools: not found
./convert-sgml: error converting to text.
make[2]: [gdam-dev.txt] Error 1 (no tiene efecto)
make[2]: se sale del directorio `/home/pattone/gdam-0.942/doc'
make[1]: se sale del directorio `/home/pattone/gdam-0.942/doc'
Making all in common
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/common'
make[1]: se sale del directorio `/home/pattone/gdam-0.942/common'
Making all in server
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/server'
Making all in plugins
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/server/plugins'
Making all in synthhelpers
make[3]: se ingresa al directorio `/home/pattone/gdam-0.942/server/plugins/synthhelpers'
make[3]: No se hace nada para `all'.
make[3]: se sale del directorio `/home/pattone/gdam-0.942/server/plugins/synthhelpers'
make[3]: se ingresa al directorio `/home/pattone/gdam-0.942/server/plugins'
make[3]: No se hace nada para `all-am'.
make[3]: se sale del directorio `/home/pattone/gdam-0.942/server/plugins'
make[2]: se sale del directorio `/home/pattone/gdam-0.942/server/plugins'
Making all in devices
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/server/devices'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/server/devices'
Making all in helper
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/server/helper'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/server/helper'
Making all in .
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/server'
test -L plugins-binary || ln -sf ../plugins-binary plugins-binary
make[2]: se sale del directorio `/home/pattone/gdam-0.942/server'
Making all in tests
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/server/tests'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/server/tests'
make[1]: se sale del directorio `/home/pattone/gdam-0.942/server'
Making all in client
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/client'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/pattone/gdam-0.942/client'
Making all in component
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/component'
Making all in plugins
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/component/plugins'
test -L server || ln -s ../../server/plugins server
test -L model || ln -s ../../component/plugins model
test -L skin || ln -s ../../skin/plugins skin
make[2]: se sale del directorio `/home/pattone/gdam-0.942/component/plugins'
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/component'
test -L plugins-binary || ln -sf ../plugins-binary plugins-binary
make[2]: se sale del directorio `/home/pattone/gdam-0.942/component'
make[1]: se sale del directorio `/home/pattone/gdam-0.942/component'
Making all in skin
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/skin'
Making all in plugins
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/plugins'
test -L server || ln -s ../../server/plugins server
test -L model || ln -s ../../component/plugins model
test -L skin || ln -s ../../skin/plugins skin
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin/plugins'
Making all in help
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/help'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin/help'
Making all in default
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/default'
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin/default'
Making all in bluetone
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/bluetone'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin/bluetone'
Making all in foreign
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/foreign'
Making all in xmmsvis
make[3]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/foreign/xmmsvis'
make[3]: No se hace nada para `all'.
make[3]: se sale del directorio `/home/pattone/gdam-0.942/skin/foreign/xmmsvis'
make[3]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/foreign'
make[3]: No se hace nada para `all-am'.
make[3]: se sale del directorio `/home/pattone/gdam-0.942/skin/foreign'
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin/foreign'
Making all in ladspa_skins
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin/ladspa_skins'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin/ladspa_skins'
make[2]: se ingresa al directorio `/home/pattone/gdam-0.942/skin'
test -L plugins-binary || ln -sf ../plugins-binary plugins-binary
make[2]: se sale del directorio `/home/pattone/gdam-0.942/skin'
make[1]: se sale del directorio `/home/pattone/gdam-0.942/skin'
Making all in gdam123
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/gdam123'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/pattone/gdam-0.942/gdam123'
Making all in defaults
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/defaults'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/pattone/gdam-0.942/defaults'
Making all in cli
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942/cli'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/pattone/gdam-0.942/cli'
make[1]: se ingresa al directorio `/home/pattone/gdam-0.942'
test -d lib || mkdir lib
for lib_spec in component:libgdam-model                 \
                        client:libgdam-client                   \
                        skin:libgdam-skin                       \
                        common:libgdam-common ; do              \
          tmpdir=`echo $lib_spec | sed -e 's/:.*$//'` ; \
          tmplib=`echo $lib_spec | sed -e 's/^.*://'` ; \
          test -L lib/$tmplib.so ||                             \
            ln -s -f ../$tmpdir/.libs/$tmplib.so lib/ ; \
          test -L lib/$tmplib.a ||                              \
            ln -s -f ../$tmpdir/.libs/$tmplib.a lib/ ;  \
          ( cd lib ; ln -s -f $tmplib.so $tmplib.so.0 ) ;       \
        done
make[1]: se sale del directorio `/home/pattone/gdam-0.942'


please HEELLLPPP!!!!!

---

