---
title: "Cannot detect network adapter (ethernet)"
date: 2008-02-21
forum: Dell  Ubuntu Support
---

### Post by rishi.lalseta on 2008-02-21
Hello all,
 
Configuration of the system
Dell r200 quad core intel xeon processor,DUAL INTEGRATED BROADCOM 5721 GIGABIT ETHERNET CONTROLLER.

I have installed properly the UBUNTU SERVER INSTALL.

When i do ifconfig it can only detect one ethernet controller.

I also used the commad lspci | grep broadcom and it shows 2 controllers

Why is the second ethernet controller not working

Other commands i tried were 
ifup etho
already configured
ifup eth1 
ignoring unknown interface eth1=eth1.

I also tested individually the network cables and works fine.

I went in 
nano /etc/network/internfaces

there it only shows eth0.

Can anyone help me how to configure the second ethernet controller

Thanks

---

