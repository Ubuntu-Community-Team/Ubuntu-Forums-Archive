---
title: "Backgrounding ifup commands if not dhcp response received"
date: 2005-08-28
forum: Desktop Environments
---

### Post by haldrik on 2005-08-28
Hi!
I have a little issue that I'd like to resolve. Basically, I use both ethernet and wireless g to connect to networks, as I move my little laptop around quite a bit. The problem I have is that if I'm using wireless today, and have wlan0 setup as the principle network adapter, I have a very long pause when booting if I happen to be away from my wireless network and use ethernet instead. If I have ethernet setup as the primary network device, then there's a long pause once I move back to wireless (after booting, I would just change my networking prefs back to wireless, but there's always that one long pause after a switch of locations.

Now I know I can just set it up to not try to log on to any networking (then of course there's a long pause when Ubuntu tries to sync the clock with some networked time service), but then I have to manually turn on whichever network device I need at that particular boot time.

Suse linux (which I used before) would simply background (but not give up) trying to get an IP address from a DHCP server if it took more than say 2 seconds to get an answer, so that the rest of the boot process could carry on while the DHCP server takes its time.

So is there a way at boot time to tell Ubuntu to first try getting an IP address from eth0, if it doesn't get one in 3 seconds to then use wlan0 instead and to background the whole process so the rest of the boot doesn't have to wait on these functions?

Thanks for any hints...

---

### Post by sigma2805 on 2005-08-28
hi, get ifplugd in synaptic. that basically will activate the ethernet and wireless connections when they are either plugged in or the wireless connection is present or else it wont. this speeded up my boot time considerably.

---

### Post by fdimmling on 2005-08-28
[QUOTE=sigma2805]hi, get ifplugd in synaptic. that basically will activate the ethernet and wireless connections when they are either plugged in or the wireless connection is present or else it wont. this speeded up my boot time considerably.[/QUOTE]

On my Hoary  system (Aver Travelmate 291LCi with builtin LAN and WLAN used with wpa_supplicant) it changes nothing, still waiting more than one minute at

configuring network

My /etc/network/interfaces looks as follows (omitting loopback interface entry)

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
# iface eth0 inet dhcp

# WLAN network interface
iface eth1 inet dhcp
pre-up ifconfig eth1 up
up /root/ssidselect eth1
post-down ifconfig eth1 down
post-down killall -q wpasupplicant

ssidselect is looking for the AP and its ssid and starting wpa_suuplicant with the appropriate key.

I guess I have to change the eth0 entry but how?

Friedrich

---

