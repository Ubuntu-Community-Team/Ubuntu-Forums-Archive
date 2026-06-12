---
title: "Big mistake: try to install beagle"
date: 2005-08-15
forum: Desktop Environments
---

### Post by stack445 on 2005-08-15
I was interested in beagle so i decide to try to install it. But ive made a big mistake. I've put debian source in my sources.list and i try to install following the debian instruction on the beagle web site. ( did not see the ubuntu link ) Of course it did not work. I also try to undo what i've done by removing the pakage that i was suppose to install, remove the debian entry in my source list and do a apt-get install.  Now everything is pretty messed up. I've got problem with local, apt keep complaining about x11-common not beeing there and my xsession wont start. ( i am using fwm for now ) . What i would like to know, is there a way to actualy re-install the default install without losing everything ? I do i fix my mistake ? 

here is some info: 

source added the remove: 

deb     [http://ftp.debian.org/debian](http://ftp.debian.org/debian) unstable main non-free contrib
deb-src [http://ftp.debian.org/debian](http://ftp.debian.org/debian) unstable main non-free contrib

pakage i try to install : 

libgtkspell-dev libglib2.0-dev mozilla-dev libexif-dev \
libgnomevfs2-dev libgnome2-dev libgconf-cil libgecko-cil libglade-cil \
libglib-cil libgnome-cil libgtk-cil libvte-cil libmono-dev mono \
gtk-sharp mono-mcs intltool gtk-doc-tools libsqlite0 libsqlite0-dev \
mono-devel mono-jay libgnomeui-dev zip docbook-utils cli-common

error message i get when i try to start a application :  (exemple firefox)

(firefox-bin:7045): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** loading the extensions datasource

error when i do apt-get install -f
Reading package lists... Done
Building dependency tree... Done
E: The package x11-common needs to be reinstalled, but I can't find an archive for it.

i dont know if someone could help me. I dont know if you need more info either. I REALY should i though twice before doing stupid thing like this...

maxime ( french guy so dont be to picky on spelling )

---

### Post by stack445 on 2005-08-15
anyone, any idea ?

---

### Post by spartas on 2005-08-15
I don't know if you'll be able to recover from that situation, becuse ubuntu does not use x11-common, which is why you aren't able to install it.  You may want to try 'sudo apt-get install --reinstall ubuntu-desktop' and see if that works for you.  Alternatively, you will want to backup all your data and reinstall.

For future reference, it's not good to switch repositories.  Also, if want beagle, you can try the instructions at [http://beaglewiki.org](http://beaglewiki.org) under Ubuntu.

---

### Post by stack445 on 2005-08-15
so, his there any windows manager that i could use. I gonna take that chance to buy a new hd, to add some space

---

### Post by Reb on 2005-08-15
You might have messed yourself up pretty badly bringing in Debian x-packages. Try apt-get install --reinstall xserver-xorg.

---

