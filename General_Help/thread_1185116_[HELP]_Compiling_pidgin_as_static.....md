---
title: "[HELP] Compiling pidgin as static...."
date: 2009-06-11
forum: General Help
---

### Post by viezz on 2009-06-11
Hi all, 
i'm still a newbie here, i tried to compile pidgin from source with static option. 

i'm using **pidgin 2.4.3**, and i'm using the following configuration option when i configure the source before i run **make**.

```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --disable-perl --disable-nss --disable-gnutls --disable-tcl --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

it works fine, after that I run **make install**, and it works to.

but when I run the application, there is no protocol available in the option when i create new IM account.
this is the screenshot:
[IMG]http://img5.imageshack.us/img5/5999/74600412.png[/IMG]

did I missed something?

this is my entire log for building pidgin:
> #1 run 

(TRIAL 1)
using:
 ```
./configure --enable-static --disable-shared --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	checking for xgettext... no
	checking for msgmerge... no
	checking for msgfmt... no
	configure: error: GNU gettext tools not found; required for intltool

conclusion:
	need GNU gettext tools (apt-get install gettext)

(TRIAL 2)
retry to configure:
```
./configure --enable-static --disable-shared --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	You must have the GLib 2.0 development headers installed to build.
	If you have these installed already you may need to install pkg-config so I can find them.

conclusion:
	need Glib 2.0 ( apt-get install build-essential libglib2.0-0 libglib2.0-dev)

(TRIAL 3)
retry to configure:
```
./configure --enable-static --disable-shared --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	You must have the GTK+ 2.0 development headers installed to compile Pidgin.
	If you want to build only Finch then specify --disable-gtkui when running configure.
	
conclusion:
	need GTK+ 2.0 development headers (apt-get install build-essential libgtk2.0-0 and libgtk2.0-dev)

(TRIAL 4)
retry to configure:
```
./configure --enable-static --disable-shared --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	XScreenSaver extension development headers not found.
	Use --disable-screensaver if you do not need XScreenSaver extension support,
	this is required for detecting idle time by mouse and keyboard usage.

conclusion:
	use --disable-screensaver for next configure

(TRIAL 5)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	Startup notification development headers not found.
	Use --disable-startup-notification if you do not need it.

conclusion:
	use --disable-startup-notification for next configure

(TRIAL 6)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	GtkSpell development headers not found.
	Use --disable-gtkspell if you do not need it.

conclusion:
	use --disable-gtkspell for next configure

(TRIAL 7)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	You must have libxml2 >= 2.6.0 development headers installed to build.

conclusion:
	apt-get install libxml2-dev


(TRIAL 8)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	GStreamer development headers not found.
	Use --disable-gstreamer if you do not need GStreamer (sound) support.

conclusion:
	Use --disable-gstreamer for next configure

(TRIAL 9)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	Meanwhile development headers not found.
	Use --disable-meanwhile if you do not need meanwhile (Sametime) support.

conclusion:
	Use --disable-meanwhile for next configure

(TRIAL 10)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --prefix=/home/viezz/Desktop/pidgin-portable/portable/

```
result:
	configure: error:
	avahi development headers not found.
	Use --disable-avahi if you do not need avahi (Bonjour) support.

conclusion:
	Use --disable-avahi for next configure

(TRIAL 11)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --prefix=/home/viezz/Desktop/pidgin-portable/portable/

```
result:
	configure: error:
	D-Bus development headers not found.
	Use --disable-dbus if you do not need D-Bus support.

conclusion:
	Use --disable-dbus for next configure

(TRIAL 12)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	Perl development headers not found.
	Use --disable-perl if you do not need Perl scripting support.

conclusion:
	Use --disable-perl for next configure

(TRIAL 12)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --disable-perl --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	Neither GnuTLS or NSS SSL development headers found.
	Use --disable-nss --disable-gnutls if you do not need SSL support.
	MSN, Novell Groupwise and Google Talk will not work without GnuTLS or NSS. OpenSSL is NOT usable!

conclusion:
	Use --disable-nss --disable-gnutls for next configure

(TRIAL 13)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --disable-perl --disable-nss --disable-gnutls --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	configure: error:
	Tcl development headers not found.
	Use --disable-tcl if you do not need Tcl scripting support.

conclusion:
	Use --disable-tcl for next configure

(TRIAL 14)
retry to configure:
```
./configure --enable-static --disable-shared --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --disable-perl --disable-nss --disable-gnutls --disable-tcl --prefix=/home/viezz/Desktop/pidgin-portable/portable/
```

result:
	Success configure

(TRIAL 15)
make the file using:
	```
make install
```

result:
	pidgin successfully build as static for some failed condition:
		no protocol support when pidgin run..


Debugging Information
  Arguments to ./configure:   '--enable-static' '--disable-shared' '--disable-screensaver' '--disable-startup-notification' '--disable-gtkspell' '--disable-gstreamer' '--disable-meanwhile' '--disable-avahi' '--disable-dbus' '--disable-perl' '--disable-nss' '--disable-gnutls' '--disable-tcl' '--prefix=/home/viezz/Desktop/pidgin-portable/portable/'
  Print debugging messages: No
  Plugins: Enabled
  SSL: SSL support was NOT compiled!

  Library Support
    Cyrus SASL: Disabled
    D-Bus: Disabled
    Evolution Addressbook: Disabled
    Gadu-Gadu library (libgadu): Internal
    GtkSpell: Disabled
    GnuTLS: Disabled
    GStreamer: Disabled
    Mono: Disabled
    NetworkManager: Disabled
    Network Security Services (NSS): Disabled
    Perl: Disabled
    Startup Notification: Disabled
    Tcl: Disabled
    Tk: Disabled
    X Session Management: Enabled
    XScreenSaver: Disabled
    Zephyr library (libzephyr): Not External
    Zephyr uses Kerberos: No

---

### Post by sdennie on 2009-06-11
That seems about the norm for "Number of times I have to type ./configure to get pidgin to configure itself on a slim system".  :)

But, I think you are misunderstand the point of --{enable,disable}-{static,shared}.  That tells the software what types of libraries it should generate, not what types of libraries it should link against.  You should be able to verify this by running "ldd" on your pidgin binary and seeing that it's dynamically linked to a bunch of stuff.  

The reason you are seeing no protocols is because the protocols are shared libraries that you've explicitly instructed pidgin not to build.  What you need to do is drop both of the static/shared configure options you are using and instead run configure like this:

```

LDFLAGS=-static ./configure <Long list of pidgin flags that should have been auto-detected>

```

That will tell the linker that you want to link against static libraries but, it may not work.  You may not have static library versions of everything you need to link pidgin and there is also no guarantee that the build process will honor your flags in a sane manner.

---

### Post by khc on 2009-06-11
if you want to build prpls statically, use --with-static-prpls= configure option

---

### Post by viezz on 2009-06-12
@sdennie
thank you for your explanation, i think i start to understand, 
when i checked with ldd, the binaries linked dynamically to system lib, but the minimal lib needed to run pidgin is libpurple CMIIW...

with :
```

LDFLAGS=-static ./configure --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --disable-perl --disable-nss --disable-gnutls --disable-tcl --prefix=/home/viezz/Desktop/pidgin-portable/portable/

```

the result is still the same, i can see no protocols available.

when i add **--with-static-prpls=yahoo**, i get this error:
> 
../../libpurple/.libs/libpurple.a(core.o): In function `static_proto_init':
/home/viezz/Desktop/pidgin-portable/pidgin-2.4.3/libpurple/core.c:72: undefined reference to `purple_init_yahoo_plugin'
collect2: ld returned 1 exit status
make[3]: *** [nullclient] Error 1
make[3]: Leaving directory `/home/viezz/Desktop/pidgin-portable/pidgin-2.4.3/libpurple/example'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/viezz/Desktop/pidgin-portable/pidgin-2.4.3/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/viezz/Desktop/pidgin-portable/pidgin-2.4.3/libpurple'
make: *** [install-recursive] Error 1


did i missunderstand something?

---

### Post by viezz on 2009-06-13
I found some reference that told me to use the latest pidgin source..
i found pidgin 2.5.6 in packages.debian.org,

i'm using the folowing configuration option:
```

LD_LIBRARY_PATH=../lib ./configure --enable-static --disable-shared --disable-nm --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-dbus --disable-perl --disable-nss --disable-gnutls --disable-tcl --libdir=/home/viezz/Desktop/portable/lib --includedir=/home/viezz/Desktop/portable/include --with-static-prpls=yahoo --prefix=/home/viezz/Desktop/portable/

```it's work fine and when i run "make", it works too.

when i run the application on another PC with debian and another one with ubuntu 8.04 fresh installed, it's work  :D , but there's something bothering me, the icon image in the application doesn't show up, so the application running with blank icon image...:(

anyone got an idea how to fix this?

---

