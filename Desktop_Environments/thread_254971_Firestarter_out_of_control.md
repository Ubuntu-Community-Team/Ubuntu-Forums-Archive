---
title: "Firestarter out of control"
date: 2006-09-10
forum: Desktop Environments
---

### Post by eugenia on 2006-09-10
Firestarter (and the file /etc/iftab) has stuffed up my whole installation of Ubuntu.

Firestarter will not start because it says "The device eth2 is not ready. Please check your network device settings and make sure your internet connection is active"

I only have eth0 and eth1.

eth0 is connected to the internet and eth1 is my local connection. There is no eth2.

How can I get rid of the eth2 that Firestarter keeps coming up with because until I do the other computers on the local network cannot connect unless I revert to booting **_Windows_**?

Total removal and reinstallation of the Firestarter package does not work.

There are no firestarter forums and the Firestarter manual has nothing that helps so I am hoping someone at Ubuntu can help me to find out where Firestarter is finding eth2 (and it is not /etc/iftab) so I can remove it.

I am at the point now that the only solution is to cfdisk and reinstall Ubuntu.

Any and all suggestions are welcome thanks.](*,)

---

### Post by 5-HT on 2006-09-10
If you can get to Firestarter's preferences menu, there is an option for stipulating the network device.
Alternatively, you could edit the config file: /etc/firestarter/configuration.
Near the top is the relevant line for the network device.

No need to even remotely consider a reinstall.
Hope that helps.

---

### Post by eugenia on 2006-09-10
Thanks a lot 5-HT, that did it. eth2 was showing instead of eth0. I usually look at configurable files using the text editor first (fstab, iftab hosts.conf etc) and as it wouldn't list it I assumed it was not configurable. However I sudo'd it and sure enough I could see the problem.

What I can't understand is why /etc/firestarter/configuration didn't change after I uninstalled rebooted and then reinstalled Firestarter. When I uninstalled using Synaptic it asks if you want to remove the package including configuration files.

Could this be a fault with apt-get uninstall and/or Synaptic?

Many thanks once again as I love Ubuntu.:D

---

