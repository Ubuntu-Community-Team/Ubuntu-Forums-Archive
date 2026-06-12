---
title: "RealVNC vncviewer on Ubuntu 9.04 AMD64"
date: 2009-10-25
forum: Desktop Environments
---

### Post by jtayl22 on 2009-10-25
FYI, for my environment (Solaris and RHEL servers inside a Cisco VPN being accessed on an Ubuntu 9.04 AMD64 laptop) the responsiveness of the RealVNC vncviewer is vastly superior to the TightVNC vncviewer that I installed from the Ubuntu distro.

To install the RealVNC vncviewer on AMD64 I needed to build from source:

$ sudo apt-get install g++
$ sudo apt-get install xserver-xorg-dev
- Download vnc-4_1_3-unixsrc.tar.gz from [http://www.realvnc.com](http://www.realvnc.com)
$ gzip -dc vnc-4_1_3-unixsrc.tar.gz | tar xvf -

Need to modify 3 source files:
1) ./unix/x0vncserver/Image.cxx
#include <cstdlib>

2) ./unix/tx/TXImage.cxx
#include <cstdlib>

3) ./common/network/TcpSocket.cxx
#include <stdlib.h>

$ cd vnc-4_1_3-unixsrc/unix
$ ./configure
$ make
$ sudo cp vncviewer/vncviewer /usr/local/bin

Hope this helps someone.

Jeff

---

### Post by jtayl22 on 2009-11-17
Tried to repeat the process, but I had some problems:

../tx/TXWindow.h:33:22: error: X11/Xlib.h: No such file or directory
../tx/TXWindow.h:34:23: error: X11/Xutil.h: No such file or directory
In file included from DesktopWindow.h:28,
                 from DesktopWindow.cxx:22:
../tx/TXWindow.h:51: error: ‘XEvent’ has not been declared

Resolved with:

$ sudo apt-get install xorg-dev

---

### Post by discofever on 2009-11-17
Nice got it work thank you !

Did you also manage to compile Xvnc ?

---

### Post by doubletruncation on 2009-12-04
Thanks for posting this! It was a life-saver for me.

---

