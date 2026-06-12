---
title: "Compiling from Source"
date: 2005-12-26
forum: Desktop Environments
---

### Post by GMathews on 2005-12-26
Im still new to ubuntu and linux.

I tried compiling the libdvdcss2 source for ubuntu breezy. How do I know if its actually installed, coz if I install a package using dpkg it still appears in synaptic but when its through ./configure and make install you dont really know?

Thanks

---

### Post by mcduck on 2005-12-26
First install 'checkinstall'. Then, when you are compiling something, instead of command 'sudo make install' use 'sudo checkinstall -D' and it will create you a .deb package that you can install with 'dpkg -i package.deb'. Then your program will show in Synaptic. This also makes it easier to uninstall compiled programs. (I think that simple 'sudo checkinstall' would automaticly install the created .deb package too..)

Edit: also, check [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic), some of the repositories listed there include libdvdcss2 so you could install it with apt-get/Synaptic.

---

### Post by GMathews on 2005-12-26
Thanks, thats a pretty beneficial command to use. :)

---

