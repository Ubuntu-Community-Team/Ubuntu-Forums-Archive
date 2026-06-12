---
title: "how to install compiz fusion plugins?"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by pacsum on 2007-09-04
I would like to know how can I install a plugin for compiz fusion I just downloaded? (3D windows)

---

### Post by patmalcolm91 on 2007-10-09
I'm also trying to do the same thing, i think all you have to do is extract the files, navigate to the extracted directory in the terminal, then type "make", the makefile automatically compiles and installs the plugin. My only problem is i get a bunch of syntax errors and a message saying to install "libxml-2.0" (which isn't even a package, there's libxml, libxml2, etc. etc., but no libxml-2.0).

---

### Post by benhur99ph on 2007-10-09
Question: Where did you download the 3D windows plugin??? I've been trying to get that for sometime now. Thanks.

---

### Post by five_13 on 2007-10-09
here's a package for all the new Compiz plugins.. enjoy

[http://www.anykeysoftware.co.uk/compiz/plugins/](http://www.anykeysoftware.co.uk/compiz/plugins/)

---

### Post by patmalcolm91 on 2007-10-09
This is what i get:

> checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ_EXTRA... configure: error: Package requirements (compiz >= 0.3.5 glib-2.0 dbus-1) were not met:

Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxml-2.0', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_EXTRA_CFLAGS
and COMPIZ_EXTRA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


It's still the same problem, there's no libxml-2.0 package installed.

---

### Post by smartboyathome on 2007-10-09
you need to install libxml2-dev. Also, you can get the 3D Windows plugin from the GIT area on opencompositing.org, but I don't know if it works without the latest version of Compiz Fusion (from the same place, not 0.6.0).

---

### Post by patmalcolm91 on 2007-10-09
thanks! that worked, but now it tells me i need "libxslt" installed, and apt-get says the package doesn't exist

EDIT: i got that taken care of, but now i get this:

> 
checking for COMPIZ_EXTRA... configure: error: Package requirements (compiz >= 0.3.5 glib-2.0 dbus-1) were not met:

No package 'glib-2.0' found
No package 'dbus-1' found


---

### Post by patmalcolm91 on 2007-10-09
i got these installed, but for some reason, the plugins still don't show up in the plugin manager ???

---

### Post by uberMongo on 2007-10-12
I'm having the same problem, the presented solution didn't solve it for me either...

---

### Post by najeer on 2007-10-29
Did anyone get a resolution to this because I just completed the above steps and I encountered the same.

---

### Post by bhencetotozo on 2007-11-01
It is not working for me neither... i did this :

wget [http://gandalfn.club.fr/ubuntu/compiz-extra/compiz-extra-latest.tar.bz2](http://gandalfn.club.fr/ubuntu/compiz-extra/compiz-extra-latest.tar.bz2)
tar jxvf compiz-extra-latest.tar.bz2
cd compiz-extra-x.x.x
./configure && make && sudo make install


then i got an error saying: :

Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ_EXTRA... configure: error: Package requirements (compiz >= 0.3.5 glib-2.0 dbus-1) were not met:

No package 'compiz' found
No package 'dbus-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_EXTRA_CFLAGS
and COMPIZ_EXTRA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

then, i went to advanced desktop effects and there are NO new plugins.. only whatever was there before

---

### Post by ilowtf on 2007-11-01
> **bhencetotozo said:**
> It is not working for me neither... i did this :

wget [http://gandalfn.club.fr/ubuntu/compiz-extra/compiz-extra-latest.tar.bz2](http://gandalfn.club.fr/ubuntu/compiz-extra/compiz-extra-latest.tar.bz2)
tar jxvf compiz-extra-latest.tar.bz2
cd compiz-extra-x.x.x
./configure && make && sudo make install


then i got an error saying: :

Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ_EXTRA... configure: error: Package requirements (compiz >= 0.3.5 glib-2.0 dbus-1) were not met:

No package 'compiz' found
No package 'dbus-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_EXTRA_CFLAGS
and COMPIZ_EXTRA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

then, i went to advanced desktop effects and there are NO new plugins.. only whatever was there before

cd compiz-extra-x.x.x
You're supposed to change the x.x.x to the version of the script

About the second error, I get a similar one and still don't know how to fix it >.<, anyone knows?

---

### Post by ovitz on 2007-11-01
Same error here. Ovitz sad.

---

### Post by w116tjb on 2007-11-03
Try this thread, it worked for me.

[3D Windows]("http://ubuntuforums.org/showthread.php?t=585491&highlight=3d+windows")

---

