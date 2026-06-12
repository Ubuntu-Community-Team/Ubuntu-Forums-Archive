---
title: "obex_test problems"
date: 2008-11-08
forum: Desktop Environments
---

### Post by frit on 2008-11-08
Hello, there.
I'm having a problem testing my cel phone usb by openobex using obex_test.

The pc knows the usb is connected, as it shows this line if I try a 'lsusb':

Bus 001 Device 002: ID 0421:043a Nokia Mobile Phones N70 USB Phone Parent


But 'obex_test -u' shows nothing:

Using USB transport, querying available interfaces
<it was supposed to have a list of usb interfaces here>
Use 'obex_test -u interface_number' to run interactive OBEX test client

I've already tried to change 020_permissions.rules in udev, but had no effect.

Anyone?

---

