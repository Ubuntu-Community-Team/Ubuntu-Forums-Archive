---
title: "virtualbox networking question"
date: 2009-05-02
forum: General Help
---

### Post by Locutus_of_Borg on 2009-05-02
running virtualbox-2.1.4_OSE and using Host networking on interface wlan0 which uses dhcp to acquire an IP, my client Windows XP Pro gets the same IP as the host.  Is there anyway to change that?

Also, and more importantly, even though the host and client use the same IP, the client still gets a unique network location or internal IP address different from my host's inet address, this is good, however this only happens when the host is connected to the internet.  If the host is off-line, the client does not get assigned a reachable network address.  (Under connection properties the client lists an IP address, but this address is not reachable from the host)

Thusly, I am only able to use samba, netbios, etc. while online.

Is there any way to resolve this issue?

Thanks.

---

### Post by zvacet on 2009-05-02
> Bridged - When you use bridged networking your guests will act as if they are on your LAN, if you use dhcp guests will get an IP address from your router for example. The disadvantage is that, with the exception of VMWare, you must manually configure your bridge and connections. You may or may not be able to bridge your wireless card.

Once you have configured a bridge you then add interfaces, starting with eth0. You then add what are called "TAP" or virtual interfaces for your guests. You can either make a tap "on demand" with wrapper scripts when starting a guest or make them persistent.

You may or may not be able to bridge a wireless card (usually not without some serious tweaking)

Taken from [here.]("http://ubuntuforums.org/showthread.php?t=973756")

---

### Post by Locutus_of_Borg on 2009-05-02
That information is for older virtualbox versions.
You no longer have to create any bridges, and host networking with a wireless card works without need of configuration.  However it only works while host is online.

With vmware, an interface is created that gets a static IP within your subnet that the client will use regardless of host's internet status

I am just wondering if such a set-up is possible with virtualbox.

Manually creating bridges and assigning them an IP doesn't seem to work, or else I am doing it wrong.

---

