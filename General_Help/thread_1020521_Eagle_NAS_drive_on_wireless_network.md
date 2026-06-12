---
title: "Eagle NAS drive on wireless network"
date: 2008-12-24
forum: General Help
---

### Post by rem- on 2008-12-24
I have a mixed wireless network with vista, mac and now my ubuntu laptop running on it. I Have a eagletech NAS drive with a 1 TB seagate drive on the network that I can see on my Ubuntu, including sub folders (sometimes), but when I click on it, network > windows network > I get nothing in the window or I can see the folders but when I click the folders same thing? I can see the folder and drive on widows and mac and the drive is a FAT file system. I've also tried mounting the folder on the NAS drive but no luck seeing the files. I can FTP into the drive and down load files from the folders??? how do I setup this drive to be a reliable file server.

---

### Post by hal8000 on 2008-12-24
You've given no details about your wireless network, or how its configured.
Your NAS device must have a static address.
Possibly your wireless LAN is DHCP and you've starting the address pool at an address higher than the NAS device.

Possibly the reason why you only see folders is that you have read only permission. 
You can create a line in your /etc/fstab to permanently set your NAS device as read/write, however someone has beaten you to it.

[http://www.marcus-furius.com/?p=59](http://www.marcus-furius.com/?p=59)

Hope that helps.

---

