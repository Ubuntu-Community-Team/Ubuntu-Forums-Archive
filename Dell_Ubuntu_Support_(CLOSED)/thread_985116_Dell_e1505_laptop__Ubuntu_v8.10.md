---
title: "Dell e1505 laptop / Ubuntu v8.10"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mcannon-gso on 2008-11-17
I have recently installed Ubuntu 8.10 from the download site. When I was done everything worked except my wlan card. I used the Ubuntu update program and downloaded the updates. After this was completed, my sound does not work, grub loader still says generic after what looked like a new kernel update and my wlan still does not work. This computer has a Dell 1390 wireless card.

Can I please guided in the right direction to fix these issues?

I am fluent in AIX Unix and am quite new to Linux.

Thank you in advance for your help and guidance..

---

### Post by coffeeaddict22 on 2008-11-18
Hi,
You need to get a few more details. 
$ lspci -nn 
will give you a listing of all your PCI stuff, and the broadcom chipset should be in there.  

For more information on the network, try 
$ lshw
.  It's a long page of all the hardware installed.  Scroll through it to find the network card, and it'll tell you the driver (if one loaded) and whether the card's got a logical name.  
The wlan driver for most broadcom cards is now on the download CD, so I'm uncertain why it hasn't been picked up.  Also you could try looking in
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
once you've figured out what chipset you've got.
The bootloader: all the major releases are generic.  I've not tried it, but if you download a cutting edge kernel it'll probably say something different.

---

