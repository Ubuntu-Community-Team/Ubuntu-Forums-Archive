---
title: "vmware workstation xp guest crash"
date: 2006-05-12
forum: Desktop Environments
---

### Post by rugge on 2006-05-12
Hello,

When I try to use bridged networking on my XP guest in VMware Workstation 5.5 for Linux the XP guest just crashes during late in the boot process. With NAT the guest boots but does not get an IP address.

Any ideas?

Kind regards,
Rutger

---

### Post by pbottjen on 2006-05-14
I'm having the same problem, was disappointed that nobody has posted a solution yet.  The xp installation would crash when it started installing the network.  I was able to finish the installation by virtually disconnecting the network device within vmware.  As soon as I virtually reconnect the network device the virtual machine crashes and powers off without any error message or prompt.

---

### Post by pbottjen on 2006-05-15
OK the crashing problem is fixed.  My laptop has a NIC and a WiFi pcmcia. When I installed vmware i was a little confused because it asked me which device i wanted to map vmnet0 to (default eth0).  I thought that meant i wouldnt be able to use my wifi.  so i changed that to wlan0.   By re-running the configuration tool at /usr/bin/vmware-config.pl i was able to respecify the device mappings (by removing the vmnet0 and vmnet2 and readding them).  After that XP would not crash with the vmware network device enabled.

---

### Post by thierrybo on 2007-04-29
Sorry to dig out an old thread. I'm just experiencing the same problem. However the last tip does not work for me. Here is what I did :

- first my ubuntu used only eth0, no wifi, and vmnet0 was bridged to eth0
- Then I added a wifi card  and my primary network connection is now ra0. As all my VMs were using NAT, no problem
- Now when I changed my XP WM to Bridge, I had no network. Normal because vmnet0 is bridged to eth0
- I ran vmware-config.pl again and then bridged vmnet0 to ra0. This is what solved the problem for pbottjen but for me I now experience the crash problem during boot process. This is the case for any guest (linux or windows).

---

