---
title: "gnome locks on startup"
date: 2007-02-21
forum: Desktop Environments
---

### Post by nunomp on 2007-02-21
hello

I've been using edgy eft + gnome+ beryl for some time but now i have this problem: gnome locks on startup, after the first icon on the splash screen appears. However, if i wait like 5 minutes it will continue to load, but will be very very unstable (windows won't open, programs won't start, etc..). i disabled beryl now, and the same thing happens with metacity...

I tried on a different kernel and worked on the first time but now it locks too. I have both kernels 2.6.17-10 and 2.6.17-11 generic. It could be something with profile, but happens the very same thing as root.

If i boot in failsafe without graphic mode and start gnome through `startx' it still locks.

I'm now using enlightenment, which i had installed before. Yet I notice some weird things, like programs taking too long to start or don't having permissions (ie. network-admin always complains i don't have permissions to use it even if I use it as root but sometimes sudo works).

any clues before I reinstall _everything_? any help would be appreciated! thanks.

---

### Post by Waappu on 2007-02-21
Hi

Try re-install graphig card drivers.

See if you can find some glue from log files:
open system->Administration->System log

---

### Post by nunomp on 2007-02-21
thank you Waappu

I don't think it is a graphic card problem, as the Nvidia logo splash screen appears etc..
I think I may have solved the problem by uninstalling compiz. I rebooted and gnome started normally. I'll try rebooting again as a different user and in the other kernel to see if it is ok.

---

### Post by loopback on 2007-02-22
Same problem here since a couple of days, but with feisty, compiz and open source ati driver. Killing compiz process unlock the desktop.

---

### Post by nunomp on 2007-02-22
uninstalling compiz didn't solve the problem after all.. i think it has to do with ndiswrapper. whenever i change from on place (one wifi network) to another, gnome stalls. then i go to failsafe and change the network and logoff, and gnome will load again. i unisntalled ndiswrapper as i wasn't using it anymore, i'll write later if it worked.

---

### Post by loopback on 2007-02-23
I don't use ndiswrapper, but I use NetworkManager. I will try to do some tests in the next few days.

---

### Post by loopback on 2007-02-23
This should put some light upon this problem:
[http://www.vanadrighem.eu/node/32](http://www.vanadrighem.eu/node/32)

---

