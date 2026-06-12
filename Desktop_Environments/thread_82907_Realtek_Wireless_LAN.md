---
title: "Realtek Wireless LAN"
date: 2005-10-27
forum: Desktop Environments
---

### Post by whsjr86 on 2005-10-27
Does Ubuntu support built in Realtek Wireless cards on laptops?  I go to configure it in Gnome and it recongnizes a wireless card there, but it does not let me try to connect or even search for a wireless connection.  Instead it loads the loop back interface.

---

### Post by az on 2005-10-27
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

and

[https://wiki.ubuntu.com/WiFiHardware](https://wiki.ubuntu.com/WiFiHardware)

I had to get the latest inf file (windows driver) from the vendor's download page to get it to work properly.

---

### Post by dbott67 on 2005-10-27
I don't know if Ubuntu supports the Realtek 'out of the box', however, you can always use ndiswrapper.

You'll need to find the Windows driver for the Realtek wifi card, and then substitute the appropriate .inf file when required.

[http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926).

-Dave

EDIT:  D'Oh!  Beaten to the punch again!  :)

---

