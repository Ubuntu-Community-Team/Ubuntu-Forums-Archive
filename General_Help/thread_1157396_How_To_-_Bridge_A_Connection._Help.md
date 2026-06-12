---
title: "How To - Bridge A Connection. Help"
date: 2009-05-12
forum: General Help
---

### Post by dragonbeast25 on 2009-05-12
Ok First of all my computer does not connect in live cd.

Windows xp, pro sp2, WBR-1310 dlink router, speedtouch home modem

ITS WIRED..... Line jack to modem WAN to Router WAN then LAN to computer. All ethernet..

In vmware i run ubuntu and i click bridged conncetion in the vmware setup (Bridged: Connected Directly to the physical network)
I tried NAT but it does not work, only bridged.

So i boot in live cd the router does not detect computer on, but any possible way to make it bridged?? Thanks i think thats the problem, And its DCHP

---

### Post by lovinglinux on 2009-05-12
I know it's not a solution, but Virtualbox has now an option to use the host network, which does not require bridging. Simply create the virtual machine and enable the network. It works flawlessly, without additional configuration.

So if you don't have a specific reason to use VMware instead of Virtualbox, I recommend using the last one. It's pretty easy.

---

### Post by bodhi.zazen on 2009-05-12
> **dragonbeast25 said:**
> Ok First of all my computer does not connect in live cd.

Windows xp, pro sp2, WBR-1310 dlink router, speedtouch home modem

ITS WIRED..... Line jack to modem WAN to Router WAN then LAN to computer. All ethernet..

In vmware i run ubuntu and i click bridged conncetion in the vmware setup (Bridged: Connected Directly to the physical network)
I tried NAT but it does not work, only bridged.

So i boot in live cd the router does not detect computer on, but any possible way to make it bridged?? Thanks i think thats the problem, And its DCHP

No, bridging your network card works because the network is working on Windows and you are using a tap device to connect to a working internet connection with a virtual network card. 

This is NOT the same thing as booting Ubuntu and configuring your actual network card. A bridge will not work in the network card (eth0) is not working.

You will need to configure your network card in Ubuntu. I can not decipher your hardware setup from the information you posted. Are you using wireless or wired ? What network card ?

---

### Post by bigboy_pdb on 2009-05-12
If you type "lshw" in a terminal (Applications -> Accessories -> Terminal) it will print your hardware information. There is a "network" section there. If you're having trouble finding it you can use the following command.

```

lshw | sed -n '/network$/,/\*/p'

```

The sed command in the code only prints the lines between the one ending with 'network' and the next line with an asterisk in it. You can use "man sed" to get a better understanding of how the sed command works.

---

