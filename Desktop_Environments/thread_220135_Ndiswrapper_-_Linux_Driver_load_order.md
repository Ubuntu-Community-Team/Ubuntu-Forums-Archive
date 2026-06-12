---
title: "Ndiswrapper - Linux Driver load order"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Grogen on 2006-07-21
Hi

I have a belkin wireless USB network adapter (F5D7050), ubuntu kernel 2.6.15-26-386, and Im having the following problems.

I was not unhappy with the pre-installed driver for this adapter as it often caused the "Network Settings" dialog to hang the PC and did not register correct signal strength (either that or its just very poor). So I installed ndiswrapper and the the windows driver for it.

I also registred ndiswrapper to load at start up.
```
$ ndiswrapper -m
```

When I boot the computer without the adapter plugged in and then plug it once X has loaded, everthing works fine and the adapter uses the ndiswrapper driver. The problem occurs when I boot the computer with the adapter already plugged in. In this case the pre-installed linux driver is assigned to the adapter and I can not get the ndiswrapper to work (note that ndiswrapper module is started).

The folowing is what I get when I plug the adapter in after booting the PC. Lines with ">" show the output of an automated script I have monitoring dmsg:
```
$ lsmod | grep usbcore
usbcore               130692  4 ndiswrapper,usbhid,uhci_hcd
```

plug in wireless USB adapter
```
> [17179969.500000] usb 2-1: new full speed USB device using uhci_hcd and address 2
> [17179969.908000] ndiswrapper: driver rt2500usb (BELKIN,07/15/2004, 1.02.00.0000) loaded
> [17179971.380000] wlan0: vendor: 'Ralink Technology Inc.'
> [17179971.380000] wlan0: ndiswrapper ethernet device 00:11:50:8a:0f:80 using driver rt2500usb, 050D:7050.F.conf
> [17179971.380000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
> [17179971.460000] usbcore: registered new driver rtusb
> [17179971.492000] ieee80211_crypt: registered algorithm 'NULL'
> [17179971.496000] ieee80211: 802.11 data/management/control stack, git-1.1.7
> [17179971.496000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
> [17179971.512000] usbcore: registered new driver islusb
> [17179982.848000] wlan0: no IPv6 routers present

```
```
$ lsmod | grep usbcore
usbcore               130692  6 islsm_usb,rt2570,ndiswrapper,usbhid,uhci_hcd
```

Notice that the pre-installed rt2570 module is now also loaded but the driver is not being used.

The folowing is what I get when I have the adapter plugged in while booting:
```
$ dmesg
......
[17179592.832000] idVendor = 0x50d, idProduct = 0x7050
[17179592.832000] INIT bRadio=1
[17179592.832000] usbcore: registered new driver rtusb
.....
[17179593.036000] usbcore: registered new driver islusb
[17179593.204000] RT25usb  Driver version 1.1.0
......
[17179594.760000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179594.804000] usbcore: registered new driver ndiswrapper
......
[17179615.704000] rausb0 (WE) : Driver using old /proc/net/wireless support, ple ase fix driver !
[17179616.080000] rausb0: no IPv6 routers present
......

$ lsmod | grep usbcore
usbcore               130692  6 ndiswrapper,islsm_usb,rt2570,usbhid,uhci_hcd
```

In this case both the ndiswrapper and rt2570 modules are loaded but the native RT25usb driver is being used instead of the ndiswrapper rt2500usb driver.

I assume this is occuring because the hardware is being detected by the kernel and assigned a driver during, or shortly after, [FONT="Courier New"]initrd[/FONT], before the ndiswrapper module has been loaded.

I tried deleting the rt2570 driver from /lib/modules/2.6.15-26-386/kernel/usb/net and running depmod -a but then the kernel just assigns a different driver to the adapter. One that doesn't work at all.

Can someone please tell me how to get the ndiswrapper drivers to load before the others.

Thanks, sorry for long post.

---

### Post by Dr. Nick on 2006-07-21
weird, I dont have that card, but had a simialr situation. You can add the bad drivers  that get loaded to the blacklist

/etc/modprobe.d/blacklist

That is a better solution then removing them since it will work after kernel upgrades, otherwise you would have to remove drivers after every update

---

### Post by Grogen on 2006-07-22
Thanks,

I will try out the blacklist. But as I said in the original post, when I deleted the driver the kernel just assigned another one that didnt even work. So basically my only option is to keep restarting and deleting/blacklisting untill the driver I want gets used.

Hopefully it wont take too many tries...fingers crossed.

Does anyone know of a more dirrect approach?

---

### Post by Dr. Nick on 2006-07-22
Yeah, Ive never had mine assignt multiple drivers like that, that is sorta wierd. 

Sorry I dont have a more drect approach, one thing you might try though is to just unplug/replug and see what driver is loaded. Doing that may negate the need to keep restarting the computer.

Hopefully someone who has had this situation chimes in with some better advice

---

