---
title: "Cannot install HP 1018 firmware"
date: 2008-06-16
forum: Desktop Environments
---

### Post by robertoneto123 on 2008-06-16
Hello,

I'm trying to install the HP1018 firmware, but no success. It is plugged in my usb port and when I turn the printer on, I get:

Jun 16 05:47:59 amelith kernel: [46764.884263] usb 5-7: new high speed USB device using ehci_hcd and address 47
Jun 16 05:48:00 amelith kernel: [46765.427343] usb 5-7: new high speed USB device using ehci_hcd and address 48
Jun 16 05:48:00 amelith kernel: [46765.970432] usb 5-7: new high speed USB device using ehci_hcd and address 49
Jun 16 05:48:01 amelith kernel: [46766.489545] usb 5-7: new high speed USB device using ehci_hcd and address 50

The driver itself is on the right dir:
# ls /usr/share/foo2zjs/firmware/
sihp1018.dl

I tryied to use the 
apt-get install foo2xjs

or the one at 

[http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com)
sudo make uninstall
make
./getweb 1018
sudo make install
sudo make install-hotplug
sudo make cups
sudo system-config-printer

What am I doing wrong?

Thanks!

---

