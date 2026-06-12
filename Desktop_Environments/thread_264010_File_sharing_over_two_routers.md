---
title: "File sharing over two routers"
date: 2006-09-24
forum: Desktop Environments
---

### Post by jlhughes on 2006-09-24
I have a Ubuntu Desktop with samba server installed.

My Ubuntu laptop can see the share when the wired network is used.

My Ubuntu laptop cannot see the share when the wireless network is used.

The wired network is 192.168.1.xxx

The wireless network is 192.168.0.xxx

I'm a newbie in this and unsure how to debug the problem.

---

### Post by wieman01 on 2006-09-24
I am a bit confused... Are you really using two routers? Is the Samba server hooked up to 2 networks, hence using 2 network devices?

Change your laptop's wireless network configuration... It needs to have the same IP range as your Samba server. Try:
> 192.168.1.xxx
Perhaps my answer does not help you but it would help if you shed some light you the exact setup of your network (including the 2 routers...).

---

### Post by dexter on 2006-09-24
When using wireless, can you ping your desktop (192.168.1.x) from you laptop (192.168.0.x). I don't think it's a Ubuntu problem, it will likely be your router.

---

### Post by jlhughes on 2006-09-24
I understand that this is NOT an Ubuntu problem. I was hoping that someone in the Ubuntu community could help me figure out what is required to get file sharing over the wireless network to the wired network working.

WAN Internet access arrives at the wired router -- 192.168.1.254

The Ubuntu desktop has a fixed IP address -- 192.168.1.17

The wireless router gets its WAN IP address from the wired router DHCP -- usually 192.168.1.101.

The wireless router's LAN IP address default is 192.168.0.1 and the DHCP hands out IPs to the laptop in the 192.168.0.xxx range.

I tried setting the wireless router's IP LAN IP to the same range as the wired. I was able to connect the laptop to the router in that range and I was able to access the router's management with the IP set in the same range as the wired router.

BUT when the wireless router is in the same range as the wired router -- 192.168.1.xxx -- I CANNOT see the wired router and therefore I cannot reach the outside Internet.

Obviously, I don't know enough about routers and networks. I am hoping that someone from this very helpful Ubuntu community who does have some experience in situations like this can help me.

---

### Post by dexter on 2006-09-24
> **jlhughes said:**
> I understand that this is NOT an Ubuntu problem. I was hoping that someone in the Ubuntu community could help me figure out what is required to get file sharing over the wireless network to the wired network working.

WAN Internet access arrives at the wired router -- 192.168.1.254

The Ubuntu desktop has a fixed IP address -- 192.168.1.17

The wireless router gets its WAN IP address from the wired router DHCP -- usually 192.168.1.101.

The wireless router's LAN IP address default is 192.168.0.1 and the DHCP hands out IPs to the laptop in the 192.168.0.xxx range.

I tried setting the wireless router's IP LAN IP to the same range as the wired. I was able to connect the laptop to the router in that range and I was able to access the router's management with the IP set in the same range as the wired router.

BUT when the wireless router is in the same range as the wired router -- 192.168.1.xxx -- I CANNOT see the wired router and therefore I cannot reach the outside Internet.

Obviously, I don't know enough about routers and networks. I am hoping that someone from this very helpful Ubuntu community who does have some experience in situations like this can help me.

The problem is that you are using two routers and your two computers have different subnets. Here is something you could try, i'm not sure if it will work for your router. Try disabling the router function in your wireless router, making it an exention of your first router. Basicly you should just the second router as an access point, when a wireless connection needs to be set up, the wireless router should ask an IP from the wired router and give that IP to the wireless laptop (the wireless router doesn't have an ip in this case). In that case both your computers are in the 192.168.1.x range and you should not have any trouble sharing files.

---

### Post by wieman01 on 2006-09-24
Silly thought... But have you tried port forwarding? So the wired router forwarding "file sharing" requests to the wireless router and the other way around? I don't see why this should not work. I think it's a port problem rather than anything else. But I may be wrong here.

---

### Post by jlhughes on 2006-09-25
SOLUTION:

OK. This fix is so simple as to be embarassing. Essentially, I needed to turn the wireless router into a dumb wireless access point. (To go with the dumb operator.)

On the wireless router, ignore the WAN settings.

Change the LAN IP address to something compatible with the existing wired network. (In my case, change it from the default 192.168.0.xxx to 192.168.1.xxx)

Turn OFF the DHCP server on the wireless router. (Wired server has DHCP running)

Most important: Plug the LAN wire feeding the wireless router into a LAN plug and NOT the WAN plug.

Everything now works.

---

### Post by wieman01 on 2006-09-25
That's more of a hardware issue then. Got your point. We could not have been of much help in this case. :-)

---

