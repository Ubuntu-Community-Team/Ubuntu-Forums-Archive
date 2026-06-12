---
title: "Post Installation Problems"
date: 2009-05-17
forum: General Help
---

### Post by iAndrew on 2009-05-17
So guys, I recently formatted my ibm t40 into Ubuntu 8.04. And I ran into some problems.

I read up on google that the ibm t40's wireless network card should work out of the box but I don't see where I can find it.

Along with that I have several problems with the audio not working.

I've tried searching "ibm t40" in the hardware/laptops but I got nothing, so unless I searched the wrong forum all help would be appreciated.

---

### Post by Yellow Pasque on 2009-05-17
It appears that the model came with a few options for wireless ( [http://www.thinkwiki.org/wiki/Category:T40](http://www.thinkwiki.org/wiki/Category:T40) ), so you have to figure out which one you have before people can help you.

If you don't know, a command like *lspci* or *sudo lshw -C network* will tell you.

---

### Post by iAndrew on 2009-05-17
[http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)

It says it's included in linux 2.6 kernel, but I don't know anything on how to activate it.

and my audio controller is intel corp 82801DB/DB L/DBM

---

### Post by Yellow Pasque on 2009-05-17
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398/)

Follow "Fred's" instructions on blacklisting. Another comment in that bug report about a thinkpad claims audio issues were also fixed. Looks encouraging.

---

### Post by iAndrew on 2009-05-18
Seemed to work. Thanks.

I'm not sure if this a hardware problem or something but I can never connect to any passworded networks for some reason.
~ any thoughts?

---

### Post by Yellow Pasque on 2009-05-18
Thought - the card doesn't support WPA, only WEP: [http://www.cisco.com/en/US/products/hw/wireless/ps458/products_qanda_item09186a008019bd57.shtml#may1](http://www.cisco.com/en/US/products/hw/wireless/ps458/products_qanda_item09186a008019bd57.shtml#may1)

---

