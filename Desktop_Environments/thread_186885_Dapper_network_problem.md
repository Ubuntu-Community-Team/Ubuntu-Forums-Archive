---
title: "Dapper network problem"
date: 2006-06-02
forum: Desktop Environments
---

### Post by predator29 on 2006-06-02
Hi,

Ok I gave it up...I'm trying to get my network up, and runnig, with no luck.
I've an Amilo A7640, with bulid in wireless, and ethernet. The wireless worked in Breezy, but with new ndiswrapper not :(
Just installed the new Dapper, from alternate cd, in text mode. At install, there were network, with ethernet, and found all of my netwoking devices.
When I installed network-manager nm-applet crached, but solved the problem, with icon reconfiguring. Now I have nm-applet, but it says it can not found any network devices. If I delet the interfaces, form /etc/network/interfaces the nm works, see my wireless card, and ethetnet too. I just pulg in the cable, it says it is connected, but I have no network.
I tryied to get Ndiswrapper to work, but with same result. My card isn't working with ndiswrapper in Dapper. I tryed to install the ndiswrapper from breezy, but it needs the previous kernel. There were everything woking in Breezy, but now I haven't got any idea how to solve this problem. Network-manager isn't working, Ndiswrapper neither...
Have _anybody_ idea how to solve problems?

----

Edit:
I've solved the first part of problem, now I've network via ethernet :) I've installed a new kernel, for my amd, and it works with this. I dunno why...
I just disaled ipv6, 'couse I've seen in dmesg, it wants to connect to an ipv6 router.
Now only Ndiswrapper doesn't work, with the package from repos. I think now I've v1.8. It worked with 1.2. I tryed to install the previous, but it needs the prrevious kernel too...

---

