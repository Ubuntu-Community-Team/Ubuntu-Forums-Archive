---
title: "Samba stops working with a fixed IP"
date: 2005-12-21
forum: General Help
---

### Post by pete on 2005-12-21
With my Ubuntu box plugged into a Linksys router and picking up an IP address via DHCP, Samba works fine.  I can access my Ubuntu home directory from my XP laptop by typing "\\machine_name\share_name" from the Run line.

The trouble starts when I switch the Ubuntu box to a fixed IP.  By default, the Linksys DHCP pool starts at .100, so I set the IP in Ubuntu to oh, say, .50, and I don't have to worry about the router giving this address out to another machine.  Everything seems fine, but now I can't access the Ubuntu box via Samba anymore, either by using the machine name or by typing in the IP address.

Set the IP back to DHCP, and it works fine again.  Anyone have an idea what's going on?  Thanks in advance.

---

### Post by djur on 2005-12-27
I'm having the exact same problem.  Samba stops functioning after I switched to a static IP.  There must be something that needs to be pointed to that static IP, but I haven't been able to find it.

---

### Post by djur on 2006-02-20
I have found a solution to this problem.  This was occuring because parts of the network were operating on a DHCP server, and other parts were static.  I managed to fix this problem by setting up a DHCP server on the ubuntu system, and disabling the DHCP server on my router.  This forces all parts of the network to seek use the DHCP server on the ubuntu system, and samba began to work again.  Be sure to use an IP address outside the useable range of the DHCP server.

---

### Post by JA2 on 2006-02-20
Hmm... maybe the subnet masking you used in your fixed IP config was different than that assigned by the router, and prevented the Ubuntu box from responding to packets sent to it.  Perhaps when you have some time, you can try it again and compare the DHCP parameters used by the router to the output of "ifconfig" & "route" on the Ubuntu box to see where the settings differ (subnet mask, default gateway, etc.)

---

