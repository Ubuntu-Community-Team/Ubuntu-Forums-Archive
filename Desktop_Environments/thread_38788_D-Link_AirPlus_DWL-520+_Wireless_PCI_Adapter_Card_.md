---
title: "D-Link AirPlus DWL-520+ Wireless PCI Adapter Card on Linux?"
date: 2005-06-02
forum: Desktop Environments
---

### Post by Paul Panks on 2005-06-02
I can't seem to get an internet connection with my D-Link AirPlus
DWL-520+ Wireless PCI Adapter Card under either Fedora Core 4 or Ubuntu
5.04.

How do I make this card compatible with Linux, and be able to connect
to the internet from Linux? The connection is secure and requires a
connection 10-digit key, which I have, and it works fine under Windows
XP.

But are their drivers for D-Link to work under either Fedora Core 4 or
Ubuntu 5.04?

Thanks,

Paul

---

### Post by thrift on 2005-06-02
Depends what chipset the card uses.  If your not aware, many manufacturers don't give out the specs on their wireless cards or make Linux drivers.

if you open a terminal and
lspci -vvv > lspci.txt

and then attach lspci.txt from your home directory so we can get an idea of what the chipset on your wireless card is, from there we can figure out if there is linux support for it.  

If there is no Linux support for it you may find ndiswrapper could work for you using the windows driver in Linux.  I've not seen it fail to work yet in my experience, but it's flaky.

Get back to us with the lspci.txt and look through the lspci.txt for you chipset yourself as well, do some hunting on google for your chipset if you can figure out what it is from the lspci.txt.  Remember it's the chipset your worried about, not the card model because many manufacturers release multiple versions of the same card that all have different chipsets and require different drivers.

---

### Post by Paul Panks on 2005-06-02
Got it to work! I went into System - > Networking and set the wlan0 to be detected. So it works now. First Linux distro I've been able to get my internet connection working on!

Is there an upgrade of Firefox 1.0.4 for Ubuntu? I noticed it's running version 1.0.2 of Firefox in Ubuntu 5.04.

Paul

---

### Post by Fab on 2005-06-02
[QUOTE=Paul Panks]Got it to work! I went into System - > Networking and set the wlan0 to be detected. So it works now. First Linux distro I've been able to get my internet connection working on!

Is there an upgrade of Firefox 1.0.4 for Ubuntu? I noticed it's running version 1.0.2 of Firefox in Ubuntu 5.04.

Paul[/QUOTE]
 first of, ubuntu was the first distro (of those i tried) that supported this card/chipset out of the box :) anyway, to get the newest firefox either enable the backports repositories (ubuntuguide.org explains how) or download the official firefox from the mozilla hompage (mozilla.org)

---

