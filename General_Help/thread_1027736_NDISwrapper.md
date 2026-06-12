---
title: "NDISwrapper"
date: 2009-01-01
forum: General Help
---

### Post by xoorath on 2009-01-01
Greetings, I am back with another issue. I tried following a number of different tutorials on getting NDISwrapper to work, but to no avail. this is the relevant hardware I'm working with:
 
> 
gigabyte GA-EP35-DS3L
belkin f5d7050
linksys wrt54g (my network is secured with a WPA2 encryption) 

I succesfuly used the following to install the driver:

> cd (directory)
sudo ndiswrapper -i BLKWGU.inf

but after this, I dont know what to do; a pointer in the right direction would be appreciated. Thanks.

-Xoorath

---

### Post by 2hot6ft2 on 2009-01-01
Looks like you'll have to find out the version or chipset for the f5d7050 since version 3000 uses the Ralink rt73 and the version 4000 uses the ZyDas zd1211b chipset.

If it's usb use lsusb
If it's pci use lspci
in a terminal.

---

### Post by 2hot6ft2 on 2009-01-01
Try this it's for version 5000 and Intrepid 8.10
[http://spikeymikey.net/2008/11/04/belkin-f5d7050/](http://spikeymikey.net/2008/11/04/belkin-f5d7050/)

---

### Post by xoorath on 2009-01-01
How should I find out the version? This is what I get from the lsusb command:

> Bus 004 Device 004: ID 050d:705e Belkin Components 

---

