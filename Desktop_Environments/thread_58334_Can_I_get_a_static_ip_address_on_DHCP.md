---
title: "Can I get a static ip address on DHCP?"
date: 2005-08-19
forum: Desktop Environments
---

### Post by ishtvan222 on 2005-08-19
Hi,

I have a home lan network with DHCP that is controlled by a Linsys router. Is there any way thet i can have my ubuntu machine always have the same ip address (192.168.1.200) instead of it always switching?

Thanks

---

### Post by Carpe Libertatem on 2005-08-19
[QUOTE=ishtvan222]Hi,

I have a home lan network with DHCP that is controlled by a Linsys router. Is there any way thet i can have my ubuntu machine always have the same ip address (192.168.1.200) instead of it always switching?

Thanks[/QUOTE]

Yeah, go to System, Admin (Or maybe prefs) and Networking to set it up.

---

### Post by ishtvan222 on 2005-08-19
Ok great, I just right clicked on ethernet connection and set it to static. 


Thanks

---

### Post by vaskark on 2005-08-19
[QUOTE=ishtvan222]Ok great, I just right clicked on ethernet connection and set it to static.[/QUOTE]
I'm in a similar situation. I have 2 machines on a LAN (dual boot XP/Ubuntu machine, and Win98 machine). I want the XP/Ubuntu machine to have an ip address of 192.168.1.101. My question is: once I change to a static ip address (in System > Admin > Networking) do I also need to set the subnet and gateway numbers? Also, do I have to change anything in my LinkSys router settings?

Thanks.

---

### Post by Oxygene on 2005-08-19
[QUOTE=ishtvan222]Ok great, I just right clicked on ethernet connection and set it to static. 


Thanks[/QUOTE]
 On some hardware routers you can set a client lease time. That is roughly said the time that a client is guaranteed to receive the same IP from the DHCP server after some client downtime.

If you assign a static IP to your client and do not turn DHCP off on your router, please check that the IP doesn't collide with the IP range of the DHCP server since that could confuse the DHCP server.

---

### Post by 2notch on 2005-08-19
Yes, very simply. A standard Linksys router's default configuration starts assigning DHCP addresses at 192.168.1.100. Simply set your network config to some address lower than that. I generally start at 192.168.1.50. It will retain this IP and never have any conflicts with other machines on your network that do have DHCP.

Here is an example of my Ubuntu net config:
Static IP = 192.168.1.50
Gateway = 192.168.1.1
Subnet Mask = 255.255.255.0
Primary DNS = (your.ISP.dns.server)
Secondary DNS = (your.ISP.second-dns.server)

You don't have to change anything in the Linksys.

Hope this helps...

vv

---

### Post by Oxygene on 2005-08-19
[QUOTE=vaskark]My question is: once I change to a static ip address (in System > Admin > Networking) do I also need to set the subnet and gateway numbers? Also, do I have to change anything in my LinkSys router settings?

Thanks.[/QUOTE]
DHCP not only distributes IP numbers to its clients, but is capable of also propagating routing information and DNS settings. This means that if you disable DHCP on your client, you are yourself responsible for setting these informations from this time on.

That said, it is worthy to state that DHCP itself it not to blame, but hardware router producers are. This is because they do not offer you the full functionality of what the standards are capable of. It is no problem for a DHCP-server to assign fixed IP's that never ever change for certain clients  (this can be done based on the ethernet addresses, known as the MAC-address of a netword card). With it, you see that it actually IS possible to have the desired functionality without losing the advantages of centralized network administration. (but unfortunately not with lowend routers)

---

### Post by wactuary on 2005-08-19
I've found that I can point my static IP settings for Gateway and DNS to my router address and things will resolve.  That way if my ISP DNS settings change, the router will update and I won't have to update the static settings at each PC location.  I don't know if this works for all routers, but it's worked on Linksys and Netgear routers I've owned.  

Chris

---

