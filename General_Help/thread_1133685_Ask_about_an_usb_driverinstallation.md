---
title: "Ask about an usb driverinstallation????"
date: 2009-04-23
forum: General Help
---

### Post by spiceoflife on 2009-04-23
Hello,

I'm trying to install an usb driver but i have this problem when i compile the driver,i have this:

zina@zina-laptop:~/Bureau/newnewnew/ti_usb_2.6-1.0$ ./configure --prefix=/home/zina/usb/

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking os type... ok
checking kernel version... 2.6.27-11-generic
checking kernel sources... found /lib/modules/2.6.27-11-generic/build
checking usb-serial.h... not found
configure: error: cannot find usb-serial.h in kernel sources


zina@zina-laptop:~/Bureau/newnewnew/ti_usb_2.6-1.0$ dmesg

[ 783.940208] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 784.131215] usb 3-1: configuration #1 chosen from 1 choice
[ 810.136220] usb 3-1: USB disconnect, address 3
[ 979.216183] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 979.407226] usb 3-1: configuration #1 chosen from 1 choice

So,please , help me!!!!!!!

---

