---
title: "make error when compiling kconfigure"
date: 2006-01-14
forum: General Help
---

### Post by Steve1961 on 2006-01-14
I wanted to have a look at kconfigure as I've heard lots of good things about it, so I downloaded the source code and ran ./configure.  There were lots of dependencies and in the end I installed kdebase, and all the qt and x developemnt libraries before it would run successfully.  So far so good.  However, when I ran make I got error messages that I'm not sure how to resolve - see below.

steve@ubuntu:~/Source_Files/kconfigure$ make
make  all-recursive
make[1]: Entering directory `/home/steve/Source_Files/kconfigure'
Making all in doc
make[2]: Entering directory `/home/steve/Source_Files/kconfigure/doc'
Making all in en
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/doc/en'
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/doc'
make[2]: Leaving directory `/home/steve/Source_Files/kconfigure/doc'
Making all in kconfigure
make[2]: Entering directory `/home/steve/Source_Files/kconfigure/kconfigure'
Making all in icons
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/kconfigure/icon s'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/kconfigure/icons '
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/kconfigure'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wund ef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subs cripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing- format-attribute -fno-exceptions -fno-check-new -fno-common  -MT konq_actions.o -MD -MP -MF ".deps/konq_actions.Tpo" -c -o konq_actions.o konq_actions.cc; \
then mv -f ".deps/konq_actions.Tpo" ".deps/konq_actions.Po"; else rm -f ".deps/k onq_actions.Tpo"; exit 1; fi
In file included from konq_actions.cc:20:
konq_actions.h:26:19: error: qlist.h: No such file or directory
konq_actions.cc:38:33: error: konq_pixmapprovider.h: No such file or directory
/usr/share/qt3/include/private/qucom_p.h:69: warning: &#8216;struct QUBuffer&#8217; has virt ual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: &#8216;struct QUType&#8217; has virtua l functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: &#8216;struct QUType_Null&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: &#8216;struct QUType_enum&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: &#8216;struct QUType_ptr&#8217; has v irtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: &#8216;struct QUType_iface&#8217; has  virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: &#8216;struct QUType_idisp&#8217; has  virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: &#8216;struct QUType_bool&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: &#8216;struct QUType_int&#8217; has v irtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: &#8216;struct QUType_double&#8217; ha s virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: &#8216;struct QUType_charstar&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: &#8216;struct QUType_QString&#8217; h as virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: &#8216;struct QUType_QVaria nt&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: &#8216;struct QUType_varptr &#8217; has virtual functions but non-virtual destructor
make[3]: *** [konq_actions.o] Error 1
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/kconfigure'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steve/Source_Files/kconfigure/kconfigure'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/Source_Files/kconfigure'
make: *** [all] Error 2
steve@ubuntu:~/Source_Files/kconfigure$

Anybody have any advice about how to proceed?

---

### Post by GeneralZod on 2006-01-14
```

sudo apt-get install libqt4-dev libkonq4-dev

```

---

### Post by Steve1961 on 2006-01-14
OK, installed those but still get these errors:

steve@ubuntu:~/Source_Files/kconfigure$ make
make  all-recursive
make[1]: Entering directory `/home/steve/Source_Files/kconfigure'
Making all in doc
make[2]: Entering directory `/home/steve/Source_Files/kconfigure/doc'
Making all in en
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/doc/en'
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/doc'
make[2]: Leaving directory `/home/steve/Source_Files/kconfigure/doc'
Making all in kconfigure
make[2]: Entering directory `/home/steve/Source_Files/kconfigure/kconfigure'
Making all in icons
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/kconfigure/icon s'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/kconfigure/icons '
make[3]: Entering directory `/home/steve/Source_Files/kconfigure/kconfigure'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wund ef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subs cripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing- format-attribute -fno-exceptions -fno-check-new -fno-common  -MT konq_actions.o -MD -MP -MF ".deps/konq_actions.Tpo" -c -o konq_actions.o konq_actions.cc; \
then mv -f ".deps/konq_actions.Tpo" ".deps/konq_actions.Po"; else rm -f ".deps/k onq_actions.Tpo"; exit 1; fi
In file included from konq_actions.cc:20:
konq_actions.h:26:19: error: qlist.h: No such file or directory
/usr/share/qt3/include/private/qucom_p.h:69: warning: ‘struct QUBuffer’ has virt ual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: ‘struct QUType’ has virtua l functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: ‘struct QUType_Null’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: ‘struct QUType_enum’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: ‘struct QUType_ptr’ has v irtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: ‘struct QUType_iface’ has  virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: ‘struct QUType_idisp’ has  virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: ‘struct QUType_bool’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: ‘struct QUType_int’ has v irtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: ‘struct QUType_double’ ha s virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: ‘struct QUType_charstar’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: ‘struct QUType_QString’ h as virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: ‘struct QUType_QVaria nt’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: ‘struct QUType_varptr ’ has virtual functions but non-virtual destructor
make[3]: *** [konq_actions.o] Error 1
make[3]: Leaving directory `/home/steve/Source_Files/kconfigure/kconfigure'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steve/Source_Files/kconfigure/kconfigure'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/Source_Files/kconfigure'
make: *** [all] Error 2
steve@ubuntu:~/Source_Files/kconfigure$

---

### Post by GeneralZod on 2006-01-14
Did you run ./configure again? If so, I don't know what's wrong; sorry :/

---

### Post by oakz on 2006-01-14
you need to install libqt3-compat-headers.

---

### Post by Steve1961 on 2006-01-14
[QUOTE=oakz]you need to install libqt3-compat-headers.[/QUOTE]


That did it.  Thanks for this.

---

### Post by mikerobinson on 2006-01-14
I am having a similar problem. I get an error when I try to `make` anything. I tried installing all the packages mentioned in this post (except libqt4-dev, which wasn't available with my apt sources - only libqt3-dev, which wanted me to uninstall 5 other packages).

Here is what I get when trying to make:
> mike@ubuntu:~/Desktop/gaim_configdir$ make
make  all-recursive
make[1]: Entering directory `/home/mike/Desktop/gaim_configdir'
Making all in doc
make[2]: Entering directory `/home/mike/Desktop/gaim_configdir/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gaim_configdir/doc'
Making all in intl
make[2]: Entering directory `/home/mike/Desktop/gaim_configdir/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gaim_configdir/intl'
Making all in m4macros
make[2]: Entering directory `/home/mike/Desktop/gaim_configdir/m4macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gaim_configdir/m4macros'
Making all in pixmaps
make[2]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps'
Making all in smileys
make[3]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys'
Making all in default
make[4]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys/default'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys/default'
Making all in none
make[4]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys/none'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys/none'
make[4]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys'
make[3]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/smileys'
Making all in status
make[3]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/status'
Making all in default
make[4]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/status/default'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/status/default'
make[4]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps/status'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/status'
make[3]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps/status'
make[3]: Entering directory `/home/mike/Desktop/gaim_configdir/pixmaps'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps'
make[2]: Leaving directory `/home/mike/Desktop/gaim_configdir/pixmaps'
Making all in plugins
make[2]: Entering directory `/home/mike/Desktop/gaim_configdir/plugins'
Making all in docklet
make[3]: Entering directory `/home/mike/Desktop/gaim_configdir/plugins/docklet'
if /bin/sh ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.././../gaim-2.0.0beta1/plugins/docklet -I../..  -DDATADIR=\"/usr/local/share\" -DVERSION=\"2.0.0beta1\" -I../.././../gaim-2.0.0beta1/src -Wall  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -g -g -O2 -MT eggtrayicon.lo -MD -MP -MF ".deps/eggtrayicon.Tpo" -c -o eggtrayicon.lo ../.././../gaim-2.0.0beta1/plugins/docklet/eggtrayicon.c; \
then mv -f ".deps/eggtrayicon.Tpo" ".deps/eggtrayicon.Plo"; else rm -f ".deps/eggtrayicon.Tpo"; exit 1; fi
if /bin/sh ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.././../gaim-2.0.0beta1/plugins/docklet -I../..  -DDATADIR=\"/usr/local/share\" -DVERSION=\"2.0.0beta1\" -I../.././../gaim-2.0.0beta1/src -Wall  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -g -g -O2 -MT docklet.lo -MD -MP -MF ".deps/docklet.Tpo" -c -o docklet.lo ../.././../gaim-2.0.0beta1/plugins/docklet/docklet.c; \
then mv -f ".deps/docklet.Tpo" ".deps/docklet.Plo"; else rm -f ".deps/docklet.Tpo"; exit 1; fi
../.././../gaim-2.0.0beta1/plugins/docklet/docklet.c: In function 'plugin_config_frame':
../.././../gaim-2.0.0beta1/plugins/docklet/docklet.c:588: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[3]: *** [docklet.lo] Error 1
make[3]: Leaving directory `/home/mike/Desktop/gaim_configdir/plugins/docklet'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Desktop/gaim_configdir/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/gaim_configdir'
make: *** [all] Error 2
mike@ubuntu:~/Desktop/gaim_configdir$     

I have filed a [bug report]("http://gcc.gnu.org/bugzilla/show_bug.cgi?id=25683"), but nobody seems to be able to help me there.

Thanks

---

### Post by Steve1961 on 2006-01-15
Most of the time errors when compiling from source happen because you need to install certain packages.  Many source packages contain info about requirements in the readme, install and configure files, but not always.  With kconfigure the only requirements were up to date kde and qt libraries, so the rest was guesswork and trial and error.  I presume you have the standard build-essential, fakeroot, debhelper, linux-headers packages installed?

---

### Post by mikerobinson on 2006-01-15
[QUOTE=Steve1961]Most of the time errors when compiling from source happen because you need to install certain packages.  Many source packages contain info about requirements in the readme, install and configure files, but not always.  With kconfigure the only requirements were up to date kde and qt libraries, so the rest was guesswork and trial and error.  I presume you have the standard build-essential, fakeroot, debhelper, linux-headers packages installed?[/QUOTE]
I was missing fakeroot and linux-headers, after installing them I still get the same error... I don't suppose it requires a reboot, would it?

---

### Post by Steve1961 on 2006-01-15
[QUOTE=mikerobinson]I was missing fakeroot and linux-headers, after installing them I still get the same error... I don't suppose it requires a reboot, would it?[/QUOTE]


No, you don't need to reboot.  Also a good idea to install dpkg-dev.  When you next try to compiule something post the output and I'm sure someone will be able to give further advice if you run into problems.

---

### Post by mvaniersel on 2006-01-15
> ../.././../gaim-2.0.0beta1/plugins/docklet/docklet.c:588: internal compiler error: Segmentation fault

I have no idea what could cause this error, but it's not just a missing dependency. This is a problem with gcc itself.

---

### Post by mikerobinson on 2006-01-15
[QUOTE=mvaniersel]I have no idea what could cause this error, but it's not just a missing dependency. This is a problem with gcc itself.[/QUOTE]
Yeah, that's what I assumed, but I have no idea how to fix it. I tried reinstalling it with apt-get, but obviously that didn't work. I downloaded the latest gcc from the website, but I can't compile it to install it.

---

