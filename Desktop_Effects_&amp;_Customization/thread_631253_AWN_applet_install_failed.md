---
title: "AWN applet install failed"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by zeller on 2007-12-04
More or less, I'm using this post as a reference for myself, however, if it helps anyone else or sparks some thought from those who know more about what needs to be done, by all means, chime in.

Upon following the install method listed on ubuntugeek.com I was able to follow along until this command:

cd awn-extras/awn-applets/awn-core-applets/

results in:

bash: cd: awn-extras/awn-applets: No such file or directory

Ok so then, I ls and it gives me:

activate-unstable-applet.patch  helloworld-applet  README-unstable-applets.txt
awn-extras-applets              README

So I decided to:

cd awn-extras-applets

Then again I ls:

acinclude.m4    config.h.in~  install-sh           Makefile.am
aclocal.m4      config.log    intltool-extract     Makefile.in
AUTHORS         config.sub    intltool-extract.in  missing
autogen.sh      configure     intltool-merge       NEWS
autom4te.cache  configure.ac  intltool-merge.in    po
ChangeLog       COPYING       intltool-update      README
compile         debian        intltool-update.in   src
config.guess    depcomp       libtool
config.h.in     INSTALL       ltmain.sh

Ah! There's the autogen.sh. Upon running it though I get the following after a long string of scripted commands and checks:

checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0
                  glib-2.0
                  dbus-1
                  dbus-glib-1
                  libsexy
                  gconf-2.0
                  gdk-2.0
                  gdk-pixbuf-2.0
                  libnotify
                  vte) were not met:

No package 'libsexy' found
No package 'libnotify' found
No package 'vte' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Ok, I don't know what that means, so I go ahead and follow the next step:

make

make: *** No targets specified and no makefile found.  Stop.

Now what?

---

### Post by zeller on 2007-12-04
Also, simply trying to run avant-window-navigator from CLI:

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

What am I missing? libawn.so.0? Can't find that in synaptic. :(

---

### Post by jnylen on 2007-12-04
> **zeller said:**
> Also, simply trying to run avant-window-navigator from CLI:

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

What am I missing? libawn.so.0? Can't find that in synaptic. :(

I encountered this problem also, and I used the following command to fix it:

**sudo ln -s /usr/local/lib/libawn.so.0 /usr/lib/libawn.so.0**

(I found that libawn.so* were installed in /usr/local/lib, which our computers didn't like for some reason.)

I'm currently in the process of installing the applets, so I'll post again in a few minutes if I encounter any problems.  However, I can go ahead and tell you that your error means you have to install a few development packages in Synaptic.  All their names should end in -dev, and they will have names similar to the ones listed in the terminal (but you might have to put lib on the front or do some searching for the exact package names.)

Since you are only missing three packages (libsexy, libnotify, and vte), I went ahead and found out the names for you.  So if you run the following command (and say yes when prompted to install any dependencies) you should be able to compile awn-extras:

**sudo apt-get install libsexy-dev libnotify-dev libvte-dev**

(Or install libsexy-dev, libnotify-dev, and libvte-dev from Synaptic, of course.)

---

### Post by zeller on 2007-12-07
Thanks, I'll look for those and install.

---

### Post by dhaupin on 2007-12-07
Thanks, worked for me.

---

### Post by indian_gamer2003 on 2007-12-08
> 
Since you are only missing three packages (libsexy, libnotify, and vte), I went ahead and found out the names for you.  So if you run the following command (and say yes when prompted to install any dependencies) you should be able to compile awn-extras:

**sudo apt-get install libsexy-dev libnotify-dev libvte-dev**

(Or install libsexy-dev, libnotify-dev, and libvte-dev from Synaptic, of course.)

Thanks, this worked me too. :popcorn:

---

