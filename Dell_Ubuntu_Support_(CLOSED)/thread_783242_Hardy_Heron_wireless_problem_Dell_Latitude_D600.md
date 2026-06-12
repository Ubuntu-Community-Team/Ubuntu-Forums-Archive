---
title: "Hardy Heron wireless problem: Dell Latitude D600"
date: 2008-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gargouille on 2008-05-05
Hardware:
Dell Latitude D600
Broadcom BCM4309 (bcm43xx)

PROBLEM:  I recently installed Hardy on top of Gusty (format & install clean) as I had problems with the upgrade not completing.  After installing I enabled the 'Broadcom B43 wireless driver' that I was prompted to install after initial setup of Gutsy.  The wireless capability worked properly, but I was unable to shutdown properly.  There was a message that kept looping and the system would not shut down:

wlan0:  CTS protection disabled (BSSID=00:1b:2f:04:1f:18)

FIX:  reinstall b43-fwcutter from Synaptic Package Manager

---

### Post by gargouille on 2008-05-05
NEW PROBLEM: now when wireless connects to router it disconnects immediately

kern.log entry:
May  5 21:25:02 Coruscant kernel: [  871.458047] wlan0: no IPv6 routers present
May  5 21:25:08 Coruscant kernel: [ 2040.265413] wlan0: deauthenticate(reason=3)

FIX:
found in Ubuntu help:

3.2.7.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---

### Post by dsterry on 2008-06-26
Making the change above in the modules helped me with my d600. So thanks, Gargouille. Nice work.

---

