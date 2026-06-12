---
title: "Dial-up ICS?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by N8MAN1068 on 2006-02-11
I'm trying to figure out how, if at all possible, to share a dial-up connection with other pc's in my room. I know, dial-up isn't my 1st choice either, but that's all I have.
Besides my Breezy box, I also have an old Win2k Advanced Server that I keep up for some reason, even though all it does is serve as storage for files I rarely access.

I do find that I need to put it online rarely, but since moving off of XP, haven't been able to set the Server nic to point to my Breezy boxes nic, and then from there to the pp0 connection.

Any pointers?

---

### Post by eriefisher on 2006-02-11
I have had a problem sharing my dial-up connection. I am unable to communicate with my modem if eth0 is active. So far I have found out that this is a routing problem. It might be corrected through iptables but I haven't tried it yet. If I deactivate eth0 and redial no problem, but as soon as I activate eth0 my connection is gone. If you find anything else please post back because I've heard of others with the same problem and no definitive answers yet.

eriefisher

---

### Post by N8MAN1068 on 2006-02-11
i'd give disabling eth0 a shot, but if I did that, then I couldn't VNC over to the Server and check it out....so thats a no-go for me.

I've found several threads where people use ICS on the XP machines so that Ubuntu can connect, but not the other way around.

The Ubuntu box will need to be the one serving DNS. The tricky part, is that the settings will change every time you dial up, and that info will need to be re-fed to the Windows boxes

I tried setting the default gateway of eth0 to the public IP of ppp0, then on the Windows box setting it's default gateway to Ubuntus eth0, with eth0 as the primary dns server, and ppp0 as the secondary...Also tried ppp0 as primary, and with ppp0's dns settings on the Windows box....no joy though.

---

### Post by eriefisher on 2006-02-11
When I used my XP box as the gateway and shared the connection I had no problems. But I am having no luck with Linux as the gateway. I've had the same problem with two distros now. The only thing I know will work is a dual pc internet sharing modem(bestnet and actiontec carry them but I'm having trouble getting one here) it connect through ethernet and uses DHCP. You can connect through your browser. Its a combination modem/router.

eriefisher

---

### Post by yourlocalnerd on 2007-07-29
This should work as long as you set all machines statically:

In terminal su to root or use sudo.

modprobe iptables_nat
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo "1" /proc/sys/net/ipv4/ip_forward

I am pretty sure this would refer dns as well however I run my own dns server so there may be issues.

---

### Post by yourlocalnerd on 2007-07-29
and now that I post I realize this is really old, sorry folks...my bad.

---

