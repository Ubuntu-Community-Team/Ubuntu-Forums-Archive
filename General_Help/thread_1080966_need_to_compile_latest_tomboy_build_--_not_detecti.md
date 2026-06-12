---
title: "need to compile latest tomboy build -- not detecting gtk and others"
date: 2009-02-26
forum: General Help
---

### Post by jimmy the saint on 2009-02-26
I need the latest build of tomboy notes on Intrepid because they FINALLY fixed the printing issues.  I kept running into missing dependencies, but solved most of them.  The one's I cannot seem to solve are given at the end of last go around:
```
checking for LIBTOMBOY... configure: error: Package requirements (gdk-2.0 >= 2.6.0
		  gtk+-2.0 >= 2.10.0
		  atk >= 1.2.4) were not met:

No package 'gdk-2.0' found
No package 'gtk+-2.0' found
No package 'atk' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBTOMBOY_CFLAGS
and LIBTOMBOY_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I know gtk is installed!  I tried searching synaptic for a package with that exact wording, but got tons and tons of results including mplayer and just about every gtk app in the repos.  How can I solve this?

Thanks

---

### Post by geraldm on 2009-02-26
either use the gtk+-2.0.pc with pkg-config OR pass the location to configure:
--with-gtk-2.0=/usr/include/gtk-2.0

Gerald

---

### Post by Yellow Pasque on 2009-02-26
If you're building from source, you need to install the -dev packages
```
sudo apt-get install libatk-1.0-dev libgtk-2.0-dev
```

---

### Post by blazemore on 2009-02-26
```
sudo apt-get build-dep tomboy
``` make sure you have source repos enabled.

---

### Post by jimmy the saint on 2009-02-26
@blazemore
will that get the dependencies for the latest unstable build?  This is not a build that is even close to being in the repos.

---

### Post by jimmy the saint on 2009-02-26
well thanks to your help I got it made (maked).  Thank You!

Now it fails checkinstall.

```
......
Installed schema `/schemas/desktop/gnome/url-handlers/note/enabled' for locale `zh_HK'
Installed schema `/schemas/desktop/gnome/url-handlers/note/enabled' for locale `hi'
Installed schema `/schemas/desktop/gnome/url-handlers/note/enabled' for locale `pt'
test -z "/usr/local/share/dbus-1/services" || /bin/mkdir -p "/usr/local/share/dbus-1/services"
/bin/mkdir: cannot create directory `/usr/local/share/dbus-1': No such file or directory
make[3]: *** [install-dbusserviceDATA] Error 1
make[3]: Leaving directory `/home/bluto/downloads/building/tomboy 13.5/tomboy-0.13.5/data'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/bluto/downloads/building/tomboy 13.5/tomboy-0.13.5/data'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/bluto/downloads/building/tomboy 13.5/tomboy-0.13.5/data'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up.../usr/bin/checkinstall: line 302: [: /home/bluto/downloads/building/tomboy: binary operator expected
OK

Bye.



```

I ran "sudo checkinstall" so it shouldn't be a permissions issue.

Any ideas?  I would prefer to use checkinstall so that I can easily go back to the standard version should this prove unstable.  It's times like these that I really appreciate the effort that goes into the repos!

---

### Post by Yellow Pasque on 2009-02-26
Try installing the libdbus-glib-1-dev package and configuring/building again.

EDIT: Actually, use the suggested build-dep command, as it's what the tomboy build guide suggests: [http://live.gnome.org/Tomboy/Developers](http://live.gnome.org/Tomboy/Developers)

---

