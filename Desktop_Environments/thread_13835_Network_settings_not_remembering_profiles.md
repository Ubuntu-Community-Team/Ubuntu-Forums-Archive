---
title: "Network settings not remembering profiles"
date: 2005-02-03
forum: Desktop Environments
---

### Post by NaughtyusMaximus on 2005-02-03
I've got Ubuntu Hoary installed on my laptop, which has both a 10/100 ethernet card, and a 54g wireless network card.  There are several different wireless networks (all with different WEP keys) that I need to connect to depending on my location.  I've added each location and the relative settings using the 'Networking' GUI tool, however it doesn't ever seem to work properly.

I don't know if it is supported or not, but on bootup, the current location is never detected, so each network device just ends up timing out when trying to get a DHCP address.  For the locations where I have a static IP set, all of the parameters are not remembered.  When I boot, I'll have to re-enter the Gateway, and sometimes even all of the information for each location.

Any ideas?

---

### Post by NaughtyusMaximus on 2005-02-05
^^

---

### Post by llamakc on 2005-02-05
```

  [ken:Lord](06:33 AM)$ apt-cache show whereami
  Package: whereami
  Priority: extra
  Section: universe/net
  Installed-Size: 428
  Maintainer: Andrew McMillan <debian@mcmillan.net.nz>
  Architecture: all
  Version: 0.3.18
 Depends: perl, debconf (>= 1.2.9), fping | iputils-ping | netbase | dhcp-clientSuggests: pcmcia-cs, fping, net-tools, iputils-arping, ifplugd, wireless-tools,resolvconf, ethtool, oops
  Filename: pool/universe/w/whereami/whereami_0.3.18_all.deb
  Size: 61076
  MD5sum: 33c8a05d9cd3d35ca9d181ee224b05a2
 Description: Automatically reconfigure your (laptop) system for a new location whereami is a set of useful scripts and a coordinating system for
   automatically re-locating your computer within the current (network)
   environment.
   .
   Typically, you would use whereami to automatically detect and
   re-configure your laptop when you move between a variety of diverse
   networks and/or docking environments.
   .
   Although whereami will work best if all of your networks assign
   addresses through dhcp, this is not a pre-requisite and the system
   allows any technique to be used to ascertain the new location with
   as little ongoing user intervention as possible.
   .
   Having ascertained the correct location, whereami will run appropriate
   (user-configured) scripts to adjust the laptop operation to suit the
   current environment.
   .
   See the man pages for more information.  You may also get useful
   assistance from the debian-laptop mailing list, which is
   frequented by several of the users and contributors.
  Bugs: mailto:ubuntu-users@lists.ubuntu.com
  Origin: Ubuntu
  
  
``` 
  
  I have successfully used this package in the past.

---

### Post by NaughtyusMaximus on 2005-02-13
Do you by any chance have a copy of your previous config files for whereami?  I have it installed, but for the life of me can't get it to actually work properly. :(

---

