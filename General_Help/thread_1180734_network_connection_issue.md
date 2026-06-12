---
title: "network connection issue"
date: 2009-06-07
forum: General Help
---

### Post by Wobblybob on 2009-06-07
Hi all,
I'm using Jaunty/Gnome desktop on a wired & wireless network and until yesterday all was fine but not the PC connected via a wire will not connect, the result of sudo lshw _C network shows
*-network [COLOR="Red"]DISABLED[/COLOR]
description: Ethernet interface
physical id:1
logical name: pan0
serial: blah blah
capabilities: ethernet physical
configuration:broadcast=y driver=bridge driverversion=2.3 firmware=NA link-y multicast=y

as I say the connection worked yesterday, if I load a live CD on the PC I can get a connection so the hardware is all ok it must be a configuration issue, can anyone point me in the right direction?.

---

### Post by kiridude on 2009-06-07
Not really clear whether you're trying to connect via a wire or wireless, but if you right click on your connections icon in your panel, you can choose which method you want - wired/wireless.

If wireless is not working, left click the same icon and enable wireless and networking.

---

### Post by Wobblybob on 2009-06-07
> **kiridude said:**
> Not really clear whether you're trying to connect via a wire or wireless, but if you right click on your connections icon in your panel, you can choose which method you want - wired/wireless.

If wireless is not working, left click the same icon and enable wireless and networking.

sorry, the PC which is not connectig wired the laptop I'm using for this post is wireless.
PC does not have a wireless connection.

---

### Post by kiridude on 2009-06-07
did you try enabling the wired connection as I suggested?

---

### Post by Wobblybob on 2009-06-07
> **kiridude said:**
> did you try enabling the wired connection as I suggested?

yep with no luck, still tells me the wired network is disconnected.

---

### Post by kiridude on 2009-06-07
How about trying a static address - that has worked for me in the past. 

Then do a: sudo /etc/init.d/networking restart

---

### Post by Iowan on 2009-06-07
Are you connecting via DHCP? I had similar [problem]("http://ubuntuforums.org/showthread.php?t=1156441").

---

### Post by Wobblybob on 2009-06-07
Thanks Kiridude your suggestion worked, I allocated it the ip address that the router has allocated it and it's let me on.

Iowan, yes I was using DCHP and I tried your suggestion with no luck, it's strange because the router is showing that it has allocated a DCHP address and when I give the PC that address as a static ip address it joins the net. I'd still like to fix the original problem and go back to DCHP allocating the address if possible.

---

### Post by Iowan on 2009-06-07
For network stability, you will want to pick a static address outside your DHCP server's range... but good to hear that you're making progress!

---

### Post by Wobblybob on 2009-06-07
> **Iowan said:**
> For network stability, you will want to pick a static address outside your DHCP server's range... but good to hear that you're making progress!

how do I work out the range?

---

### Post by Iowan on 2009-06-08
Easiest way is to use a browser to access the router's configuration page.  Not so easy if it's not your router...

---

