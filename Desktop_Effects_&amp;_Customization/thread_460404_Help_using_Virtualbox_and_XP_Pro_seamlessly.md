---
title: "Help using Virtualbox and XP Pro seamlessly"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by QuarlesLT on 2007-05-31
I followed this HOWTO, using Feisty:

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

I am using eth0 that is static, not dhcp. First I followed the guide normally, using the steps listed. However, when I log into Windows, the LAN says it is aquiring an address for a few minutes, then says limited or no connectivity. Then I tweaked my rc.local file according to another user in that thread. Here is my current rc.local:

tunctl -t tap0 -u lamar
chmod 0666 /dev/net/tun
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
ifconfig br0 192.168.1.21 netmask 255.255.255.0 up
route add default gw 192.168.1.1 br0
brctl addif br0 tap0
ifconfig tap0 up

But when I log into Windows, the same thing happens, and I have no connectivity. Under my VirtualBox settings, I have the networking set to host and the name is tap0. The Internet on the host machine works fine.

Any help would be greatly appreciated.

---

### Post by Unicast on 2007-06-01
I had this problem, but in the end I gave up trying to get the remote desktop to work and just used NAT in Virtualbox network settings and voila you can connect to your network / internet using XP in Virtualbox.

Install "Guest Additions" in Virtualbox to get XP running fullscreen & borderless.

You can also get USB in XP working by using this wiki: [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox) (404'ing at time of posting!)

---

### Post by QuarlesLT on 2007-06-01
Bump.

---

### Post by Unicast on 2007-06-02
How rude!

I try to help and you just ignore my post.

Whatever!

---

### Post by bodhi.zazen on 2007-06-02
> **QuarlesLT said:**
> I followed this HOWTO, using Feisty:

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

I am using eth0 that is static, not dhcp. First I followed the guide normally, using the steps listed. However, when I log into Windows, the LAN says it is aquiring an address for a few minutes, then says limited or no connectivity. Then I tweaked my rc.local file according to another user in that thread. Here is my current rc.local:

tunctl -t tap0 -u lamar
chmod 0666 /dev/net/tun
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
ifconfig br0 192.168.1.21 netmask 255.255.255.0 up
route add default gw 192.168.1.1 br0
brctl addif br0 tap0
ifconfig tap0 up

But when I log into Windows, the same thing happens, and I have no connectivity. Under my VirtualBox settings, I have the networking set to host and the name is tap0. The Internet on the host machine works fine.

Any help would be greatly appreciated.

I am not sure, just a guess ...

I think the last line needs to read :

> ifconfig tap0 0.0.0.0 promisc

---

### Post by QuarlesLT on 2007-06-03
> **Unicast said:**
> How rude!

I try to help and you just ignore my post.

Whatever!

I'm sorry! But I did what you said and it works, but I'm trying to get everything seamless.

---

### Post by QuarlesLT on 2007-06-04
> **bodhi.zazen said:**
> I am not sure, just a guess ...

I think the last line needs to read :

           ifconfig tap0 0.0.0.0 promisc

Nope, still no luck.

---

