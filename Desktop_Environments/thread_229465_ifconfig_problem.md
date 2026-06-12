---
title: "ifconfig problem"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Ivan Wagner on 2006-08-04
Hi to all,

when typing the command ifconfig I only get the irda0 and eth1 interfaces (not eth0 and loopback interfaces). As a matter of fact when I want to bring up an interface I use dhclient interface_name. I doesn't work using ifup interface_name it tells me that it cannot find the interface.

This started to happen since I moved to Dapper.

Can someone guide me?

Thanks in advance,

Ivan

---

### Post by ciscosurfer on 2006-08-04
Go to System > Administration > Networking > Connections Tab and make sure the interfaces are active.  Also, at the bottom, check to see which interface is the default gateway. Come back here to post when you find out.

---

### Post by Ivan Wagner on 2006-08-04
Ok, I just changed the wireless settings changing to automatic connection at bootup with dhcp, ESSID and WEP.

Now with ifconfig the 'lo' is there and localhost works fine...

But at a command level (bash) what changed?

Thanks,

Ivan.

---

