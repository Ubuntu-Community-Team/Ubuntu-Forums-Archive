---
title: "Pxe Booting Centos 7 dvd"
date: 2016-09-06
forum: Fedora/RedHat and derivatives
---

### Post by dureal99d on 2016-09-06
I have tried every combo I can think of to get this dvd to pxe boot. I currently run FOG as a pxe server. I boot many Linux distros but cannot boot Centos as its extracted dvd structure is different.

 I do manage to get some of it to boot but then I get the dreaded dracut-initqueue 437 - dev/nfs device not found.

 I have exported the nfs and everything. I am using ipxe not PXELinux. as that is the fog preference.

 oh and I am running Fog on a Ubuntu 16.04.1 server. I realize this is a cent os forum but I come here because it is a cent os dvd I am trying to boot via pxe so I figure you would know what I should do to get it booted.

 here is my boot code, 

 kernel http://${fog-ip}/fog/service/ipxe/fedora/images/pxeboot/vmlinuz 
 initrd http://${fog-ip}/fog/service/ipxe/fedora/images/pxeboot/initrd.img
 imgargs vmlinuz root=/dev/nfs boot=live netboot=nfs nfsroot=${fog-ip}:/var/www/fog/service/ipxe/fedora/ locale=en_US.UTF-8 keyboard-configuration/layoutcode=la mirror/country=US
 boot || goto failed
 goto start

 what am I doing wrong? please help!

---

### Post by howefield on 2016-09-06
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

