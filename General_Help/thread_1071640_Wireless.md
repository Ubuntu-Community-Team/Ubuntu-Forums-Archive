---
title: "Wireless"
date: 2009-02-16
forum: General Help
---

### Post by Nathanv.1 on 2009-02-16
I have just installed Ubuntu onto my laptop but i am having a problem turning on my wireless. I push the button that usually enables the wireless, but is still not turning on. I own a Compaq presario CQ50. When i type in ```
lspci -vvv
``` and received this for my wireless.  ```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 17
	Memory at 92600000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath_pci

```
is there a way to turn it on with pushing the button?

Thanks in advance.

---

### Post by azzamite on 2009-02-16
I think the driver for your card is called madwifi,
install it, reboot and try again.

---

### Post by Nathanv.1 on 2009-02-16
I tried 2 install madwifi for ubuntu, but sadly the button still is not activating the wireless still. Anything else? i also installed ndiswrapper, but still no help. I did some more research and figured out that ubuntu doesnt recognize my wireless is even there. I think that i need to turn it on for it to recognize it. so, back to my original question. Anything else?

---

### Post by Nathanv.1 on 2009-02-24
I guess no one knos the answer

---

### Post by CrucifiedEgo on 2009-02-24
Can you post for us the output of the following commands?

ifconfig (this lists all your network interfaces and their status
iwconfig (same, except detailed information on wireless cards
lsmod (lists all installed Kernel modules)

This should help quite a bit in narrowing down the issue.

---

### Post by Nathanv.1 on 2009-02-24
alrite, hear they are:

```
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1d:72:7a:17:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2987000531 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4092 (4.0 KB)  TX bytes:4092 (4.0 KB)
iwconfig:
	lo        no wireless extensions.

	eth0      no wireless extensions.

	pan0      no wireless extensions.
lsmod:
	wlan                  211952  1 ath_pci

```

if you need the rest of "lsmod" then tell me the stuff u need,, thank you so much.

---

### Post by CrucifiedEgo on 2009-02-25
ah-HA!  You have the same wifi card i do.  Unless you feel like recompiling your drivers every time there's a kernel update, madwifi won't work (the version in the repos doesn't support our card.)

Usually I can get it to work by adding the following two lines to /etc/modprobe.d/blacklist: (use 'sudo gedit /etc/modprobe.d/blacklist' at a terminal)

```
#blacklist ath_pci and related, they don't work on AR242x
blacklist ath_pci
blacklist ath_hal
```

Usually, this allows it to "just work" by loading the correct driver.  However I had some problems this time, and had to use madwifi.  I'd suggest installing ndisgtk and using the GUI -- it's much simpler than the command line crud.

---

### Post by binbash on 2009-02-25
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by Nathanv.1 on 2009-02-25
Thank you so much  guys, it is working and it feels good to be using the internet on ubuntu again. Thx.

---

