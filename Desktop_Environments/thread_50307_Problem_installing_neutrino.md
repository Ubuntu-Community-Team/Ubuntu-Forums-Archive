---
title: "Problem installing neutrino"
date: 2005-07-19
forum: Desktop Environments
---

### Post by bidon on 2005-07-19
Hi,

I have this program neutrino for my Creative mp3 player that I'd like to install but I have a weird problem....

When I type ./configure, everything goes fine unitill this error shows up : 


checking for GLIB - version >= 2.0.0... yes (version 2.6.4)
checking for libgnome-2.0 >= 1.102.0                             libgnomeui-2.0 >= 1.102.0                               gthread-2.0 >= 1.3.7                   gtk+-2.0 >= 2.6.0                                        libxml-2.0 >= 2.4.3    libglade-2.0 >= 1.99.2                                   gconf-2.0 >= 1.1.1     gdk-pixbuf-2.0 >= 1.3.7... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

configure: error: Library requirements (libgnome-2.0 >= 1.102.0                 libgnomeui-2.0 >= 1.102.0                                gthread-2.0 >= 1.3.7   gtk+-2.0 >= 2.6.0                                        libxml-2.0 >= 2.4.3    libglade-2.0 >= 1.99.2                                   gconf-2.0 >= 1.1.1     gdk-pixbuf-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.




The thing is I allready have these libraries installed (at least I think so).

Thanks for helping

---

### Post by Xian on 2005-07-19
Do you have the libgnomeui-dev pkg installed?

---

### Post by bidon on 2005-07-20
Okay thanks,

i had the libgnomeui installed but not libgnomeui-dev.... :roll: 

thanks for helping... :)

---

