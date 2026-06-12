---
title: "Need help with network; please take a look."
date: 2009-02-09
forum: General Help
---

### Post by GARoss on 2009-02-09
Below are my previous post under Networking & Wireless.

I'm really close, I believe, but need extra advice. This is where I'm at. My XP computer DOES network to my new Ubuntu computer, but I cannot network from the Ubuntu to the XP. From Places>Network>Windows Network I DO NOT see anything upon double-clicking Windows Network. I believe, sudo gedit /etc/samba/smb.conf command indicates NO workgroup listed & that it needs to be added by editing. 
Please take a look.
I appreciate all advice.
George
 

[http://ubuntuforums.org/showthread.php?p=6704425#post6704425](http://ubuntuforums.org/showthread.php?p=6704425#post6704425)

Here's a list under Networking;

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = yes

---

### Post by cmnorton on 2009-02-14
Take a look at smbclient as a connection model. You should be able to connect, but you need to provide your XP domain credentials to do so.

---

