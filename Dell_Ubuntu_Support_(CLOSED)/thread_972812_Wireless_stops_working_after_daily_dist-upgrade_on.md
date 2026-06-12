---
title: "Wireless stops working after daily dist-upgrade on 5/11/08"
date: 2008-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madarcher on 2008-11-06
My Inspiron 1525n was working quite really well until last week when I upgraded to Intrepid and my webcam stopped working.

I installed the daily updates (through update manager) last night and my wireless (Intel wireless pro golan I think) stopped working.

By stopped working both of these no longer appear in lsusb, or lspci.  ifconfig only shows lo and eth0 (wired) wlan0 has disappeared.  /etc/network/interfaces only has an entry for lo so I assume (incorrectly probably) that eth0 and wlan0 were previously dynamiclly configured.

I assume that this is due to the upgrade of linux-image to 2.6.27.7 but update manger seems to have removed my earlier kernels from /boot and grub so I can't even start an older kernel to prove that it is not hardware failure.

I am not on my ubuntu machine at the moment but can probably get info from it later.  Can anyone help me here?  Is this a known problem?  Perhaps I need to backup my stuff and then go back to hardy with a clean install :(

John

---

