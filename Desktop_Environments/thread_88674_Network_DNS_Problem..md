---
title: "Network DNS Problem."
date: 2005-11-10
forum: Desktop Environments
---

### Post by chanorange on 2005-11-10
Hi there. I'm new to ubuntu after using Suse for a bit. Its similar but alot of things are pretty new to me.

Im having a problem with one thing though. I have an Ethernet DSL modem that keeps setting my Primary DNS to 192.168.1.1.

I have tried to enter my 'Actual' Primary and Secondary DNS through 'system, administration, networking' and through 'etc/resolve.conf'. This works for a while but it eventually resets back to 192.168.1.1. It also resets back to this if i reboot.

I Have found this thread [http://ubuntuforums.org/showthread.php?t=7280](http://ubuntuforums.org/showthread.php?t=7280)

Apprently i have to edit '/etc/dhclient.conf' to include my 'pri' and 'sec' DNS servers.

This file does not exist in this location though. A file of the same name does exist in '/etc/dhcp3/dhclient.conf' but modifying it doesnt change anything. The DNS still resets back to 192.168.1.1

My question is: Is there anyway to save my 'Actual' DNS servers? Or do i have to keep re-entering them every 15 minutes or so?

Sorry for the long post, i just wanted to make sure i crammed everything in. Thanks

---

### Post by jvictor on 2005-11-10
Y dont u disable DHCP and use a static ip if possible ?

---

### Post by chanorange on 2005-11-11
[QUOTE=jvictor]Y dont u disable DHCP and use a static ip if possible ?[/QUOTE]

Thanks for the reply. Ive just bought a Static IP from my ISP. (I had to pay £3 to get one assigned). Its working good now thanks

---

### Post by mgor on 2005-11-11
try creating /etc/dhcp3/dhclient-enter-hooks.d/resolv with the following content:
```
make_resolv_conf() {
# doing nothing.
}
```

and then edit /etc/resolv.conf manually.

---

### Post by chanorange on 2005-11-11
[QUOTE=chanorange]Thanks for the reply. Ive just bought a Static IP from my ISP. (I had to pay £3 to get one assigned). Its working good now thanks[/QUOTE]

Well the static IP only worked until i rebooted, now it wont work. So im back to dhcp and typing in the dns servers all over again.

[QUOTE=mgor]try creating /etc/dhcp3/dhclient-enter-hooks.d/resolv with the following content:
Code:

make_resolv_conf() { # doing nothing. }


and then edit /etc/resolv.conf manually.[/QUOTE]

I will try this and let you know.

---

### Post by chanorange on 2005-11-11
[QUOTE=mgor]try creating /etc/dhcp3/dhclient-enter-hooks.d/resolv with the following content:
```
make_resolv_conf() {
# doing nothing.
}
```

and then edit /etc/resolv.conf manually.[/QUOTE]

That didnt do anything :( 

Anybody else know what i can do to stop the DNS clearing?

---

### Post by stevea1210 on 2005-11-11
This wasn't mentioned, but do you have a router betwen your modem and your pc?  192.168.1.1 would be an internal ip, not an extermnal, and is a common default ip for a router.  If you are using a router, and dhcp in the router is set to use 192.168.1.1 for the dns server, it makes sense why that is coming up as your dns server.  Any dns requests that the router can't resolve, would be forwarded to the dns servers your isp assigns via its dhcp server.  It shouldn't cause any issue with you resolving external names.

When your dns server is set to 192.168.1.1, are you having issues with resolving?  Can you ping google.com for example?

---

### Post by chanorange on 2005-11-11
No i dont have a router, i just have a linksys ethernet modem. 

I don't have any problems resolving with 192.168.1.1 set as the primary dns, also Gaim works and so does the google notifier. But firefox and synaptic wont work with 192.168.1.1 set as the Primary dns.

---

### Post by professor_chaos on 2005-11-11
I'm having the same problem. To solve it, I first manually edited /etc/resolv.conf with the DNS servers and then changed the file attribute of /etc/resolv.conf to make it non-editable by....
```

sudo chattr +i /etc/resolv.conf
```

The only problem is that when booting in breezy, the resolving network hangs and I have to hit ctrl+d to skip. I wish there was a better way.

---

### Post by slux on 2005-11-12
I'm not sure about what the actual problem here but I had a bit similar problem with my WLAN AP (Apple Airport Graphite) configured to deal out IPs with DHCP and NAT them. The AP's DHCP offer lists itself as the DNS server but GNU/Linux systems can't get a reply when asking even though Windows and Mac OS X are both fine with it. I've had to configure my dhclient in this way:

```
supersede domain-name-servers 62.148.192.130;

```

This way the DHCPOFFER gets overridden for the DNS part and I don't need to edit resolv.conf all the time or anything like that. :P

---

