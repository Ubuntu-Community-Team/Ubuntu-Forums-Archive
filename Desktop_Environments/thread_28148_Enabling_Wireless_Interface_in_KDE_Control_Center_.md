---
title: "Enabling Wireless Interface in KDE Control Center problem"
date: 2005-04-19
forum: Desktop Environments
---

### Post by griphiam on 2005-04-19
I am using a laptop with a built in ethernet port and I'm using a PCMCIA wireless card (D-Link).

When I boot the computer with the wire connection (w/o the card) everything works.  When I boot with the wire and the card, the wire is default and the card (eth1 wireless) is disabled.  However, if I try to "enable" the interface in Control Center -> Network Settings -> Administrator Mode, it goes from a red X to a green check for about 1 second before going back to the red X.  The same thing happens when I hotplug the card after booting.  It appears in the Network Settings, but it won't let me enable it.  It starts to, and then falls back to disabled.

Has anyone run into this or know a way around this?

Thanks!

---

### Post by skyvoid on 2005-06-19
Hey, have you solved this? I have exactly the same problem.
I have 2 interfaces showing up on Control Center (eth0 for LAN is currently enabled), but when I tried to disable eth0 and enable eth1 (for wireless) it 
fails for some reason. iwconfig gives me some information about eth1, but there seems no traffic going on. Any ideas?

---

### Post by recover82 on 2005-06-19
what cards (i see you mentioned the dlink)..but what chipset does that use?
my linksys wpc54g (w/ speedbooster) does the same thing.  enables..then disables 1 to 2 seconds later.

-recover82-

---

### Post by Phoenix590 on 2005-06-19
Yep I've been  suffering the same problem with kubuntu... ](*,)  its like ramming your head into a wall, because I have set up the drivers for my DWL-510G (D-Link) with NDISwrapper, modprobed it, set up the wireless config, and when i go to enable it under network/internet in kcontrol, like you said, it turns green for about half a second then goes back to red..can someone please help?

---

### Post by Uta on 2005-06-21
I found this info very useful setting up my D-Link card for my laptop.

/etc/network/interfaces is the file where your network interfaces are defined, eth0 being the standard wired interface. To make the wireless network come up when you start your computer put # in front of 'auto eth0' (to stop it automaticaly starting) and add something like the following lines.

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid   MYNETWOTK
wireless_key     FEFEFEFEFE
wireless_channel 11
wireless_mode    managed

This is taken from the Wiki Howto:
[https://wiki.ubuntu.com//WiFiHowto](https://wiki.ubuntu.com//WiFiHowto)

Good Luck!

---

### Post by Miscellaneous on 2007-06-05
Hi,

I am having the same problem, and the above trick didn't work for me. Did it work for you? Have you found a solution yet?

Thanks

---

