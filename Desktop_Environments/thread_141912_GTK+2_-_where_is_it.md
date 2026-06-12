---
title: "GTK+2 - where is it?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by Vinze on 2006-03-09
Hey, I got this error when trying to compile giftui: > checking for gtk+-2.0 >= 2.2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


I have no idea how this is named in the Ubuntu repository... I'm using Xubuntu Dapper.

How would this be named? Thanks in advance.

---

### Post by lamego on 2006-03-09
It should be libgtk2...

---

### Post by kaamos on 2006-03-09
Search for gtk in synaptic and install a package that has a "2" and a "-dev". :)

---

### Post by ComplexNumber on 2006-03-09
its basically looking for a .pc file thats found in /usr/lib/pkgconfig or /usr.local.lib/pkgconfig. it looks in here to see if a particular package is installed or not. .pc files only come with the 'devel' packages (eg gtk2-devel). the error may be to do with /usr.local.lib/pkgconfig not being in the PKG_CONFIG_PATH.

---

### Post by Vinze on 2006-03-09
Hmm.. Well I'm not at my computer at the moment, I believe I have GTK 2 installed, but I probably need the development version. I'll post the results :D

---

### Post by ComplexNumber on 2006-03-09
[quote=Vinze]Hmm.. Well I'm not at my computer at the moment, I believe I have GTK 2 installed, but I probably need the development version. I'll post the results :D[/quote] install gtk2-devel. that will then install a .pc file in the pkgconfig directory in /ust/lib.  then the sources that you're compiling will be 'see' that gtk2 is installed and it will also tell it where to find it.

---

### Post by Vinze on 2006-03-10
OK, it worked, thanks :D 

I got a problem with make, but I'll post a new topic for it as it's a whole other problem...

---

