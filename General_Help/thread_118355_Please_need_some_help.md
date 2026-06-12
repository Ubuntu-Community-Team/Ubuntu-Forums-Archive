---
title: "Please need some help"
date: 2006-01-16
forum: General Help
---

### Post by oscar.romero on 2006-01-16
I'm looking a way to configure my wifi card to connect itself at the bootup. I tried everything... I do this command everytime that I bootup: **sudo ifup eth2** ;) 
Instead of going in the System/Administration/Networking and activate my card. This is not the end of the world but it's very anoying. :mad: 

Here's my configuration in /etc/network/ interfaces :
> # The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth2

iface eth2 inet dhcp
wireless-essid ******
wireless-channel 5
wireless-key *******

auto eth2


Anyone can help me with this problem? :confused:

---

### Post by joft on 2006-01-17
Hi,

I am not sure of this, but did you try to specify "eth2" together with "lo" on the "auto ..." line?

Do you use an externel (CardBus, USB, ...) wifi card or is it an internal one? If it's external your configuartion should work, but with an internal card, the kernel module might get loaded before the hotplug system is really active. At least, I had a similar problem ...

---

### Post by joft on 2006-01-18
Hi,

sorry, I just look at your post again and saw that you already specified "auto eth2" at the end - sorry. Then I don't know whats wrong with your setup.

What does syslog say about this? Perhaps there is an error during boot? (/var/log/syslog)

---

