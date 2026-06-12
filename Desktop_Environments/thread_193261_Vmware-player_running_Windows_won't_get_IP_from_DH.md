---
title: "Vmware-player running Windows won't get IP from DHCP"
date: 2006-06-09
forum: Desktop Environments
---

### Post by thomasged on 2006-06-09
Hello :)

I'm having an issue with vmware-player, running a windows(same result in XP and 2000) image. I installed it using most of the default options, during the network installation part. 

Everything works perfectly apart from the network card (It finds it as a AMD PCNet Family PCI Ethernet card in Windows). It can't get any IP from the DHCP server. 

This is what I did:

First I installed vmware-player and created an WindowsXP image, following this guide: 

[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

Then I apt-get'ed "vmware-player-kernel-modules". 
And well, to be extra secure, I modprobed vmnet and vmmon. But none of it helped, I also tried to set an static IP in the guest OS, but it diddn't help anything. 

Anyone with a suggestions to fix my issue?

(And yes, english isn't my native language)

---

### Post by olsonar on 2006-06-09
try using NAT rather than bridged. i couldn't get DHCP to work until i did that.

---

### Post by thomasged on 2006-06-09
I can't choose not to use bridged network during the installation :/

---

### Post by olsonar on 2006-06-10
don't have to. when the vm is running, click the icon on the toolbar the represents the ethernet card, and choose NAT. as long as u enabled NAT during the install, that should work fine.

---

