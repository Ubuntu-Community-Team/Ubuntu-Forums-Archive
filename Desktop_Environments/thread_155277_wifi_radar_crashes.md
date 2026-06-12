---
title: "wifi radar crashes"
date: 2006-04-04
forum: Desktop Environments
---

### Post by lbmounse on 2006-04-04
I'm running Breezy on my laptop.   I was able to get my Trendnet wireless running with ndiswrapper.   It works just fine, even automatically connects when I boot up. (most of the time)   When it does not, I am able to get it connected with wifi radar.

If it looses the connection, and i use wifi radar to reconnect, it will just sit there looking for an ip address and never find one.   It stops responding, and I am forced to stop it manually.   If I restart it and try to reconnect, it will do the same thing.   I am forced to reboot to reconnect.

Last night, it caused my entire system to hang.

What should I do?
Is there any alternative to wifi radar?

---

### Post by offchance on 2007-10-12
I have the same problem. Wifi-radar runs slowly and my laptop hangs only when running wifi-radar.

I'm using a broadcom+ndiswrapper, network manager* 0.6.4-6, and wifi-radar 1.9.8 (not from synaptic).


*edit: I disable this before using wifi-radar

---

### Post by eurgain on 2007-10-12
Are you certain that this is a problem with WiFIRadar, rather than with ndiswrapper?

From your brief description, it seems more likely that the wireless driver is failing to tell WiFIRadar anything useful, rather than WiFiRadar itself breaking, since if it were broken, its brokenness should not survive a simple program stop and re-start.  If a re-boot is needed, the problem is probably in kernel-space.

Out of interest, what does WiFiRadar offer you that NetworkManager does not?

I think that ndiswrapper is really just an emergency lash-up rather than a way to use a network device for serious work, so the real solution is probably to buy a better wireless device.  There are a whole bunch of wireless devices that work with native linux drivers, that will make you life *so* much easier.  See [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) for examples

HTH
A

---

### Post by offchance on 2007-10-12
thanks but no thanks, eurgain. I don't think I'll be cracking open my laptop to replace the wireless device any time soon.

about wifi-radar: it shows me the same networks as network manager, but it does a better job of getting connected to them. it worked like a charm at the beginning but has gradually decreased in terms of speed of performance as an application (the connection speeds are a-ok).

---

### Post by eurgain on 2007-10-12
I did not realise that it was internal!  I am sorry for you.
 
> thanks but no thanks, eurgain. I don't think I'll be cracking open my laptop to replace the wireless device any time soon.

As it happens, it is often very easy to replace the WiFi device.  You don't need to "crack open" the laptop; just open a little panel, pull out the old and slot in the new.  My experience with Dell, Toshiba and HP is that you can download very detailed instructions from the manufacturer's web site that show exactly how to exchange a wireless card. They are not particularly reliable things, so they often need to be replaced in service anyway; the manufacturers know this, so make them easy to swap.

For an internal card, if your machine uses mini-PCI, get an Intel IPW2200.  It will give you faultless IEEE802-11G connectivity with 100% native Linux drivers.

If your *really* do not want to get involved with the hardware, use a PC-Card or (*in extremis* USB device), and forget about the internal Windows-only rubbish.

Anyway, what have you got to loose? The thing does not work as it is, so it could be only very slightly more useless even if you drove your car over it!

HTH
A

---

### Post by offchance on 2007-10-13
that is hard to hear but nonetheless useful.

let's suppose, though, that my broadcom wireless card is welded permanently to my laptop and that removing it would cause the whole unit to explode and seriously injure anyone involved in the removal. what advice is there that will make wifi-radar not crash one's computer?

---

