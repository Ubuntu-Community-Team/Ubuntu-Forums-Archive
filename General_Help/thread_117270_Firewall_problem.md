---
title: "Firewall problem"
date: 2006-01-14
forum: General Help
---

### Post by htlh on 2006-01-14
Hi! 

After hearing all good things `bout Linux, I ended up installing Ubuntu this afternoon.

Had some problems with my wireless connection, but fixed it after reading a post here on the forum (Thanks!)

But back to topic.

I manage to hook up to the router, but I cant manage to get on the Internet.
I think it might be a firewall-related issue, but I cant seem to find out how to turn off the firewall or if I even have a firewall installed.
Anyone has any ideas? Help?

Thanks.

---

### Post by BathroomNinja on 2006-01-14
Unless you installed a firewall, then you shouldn't have any issues with one.  However, it's possible that your router may be blocking your access.  Could be many things.  I take it you are connected via wireless to your router. 

Pull up the terminal and type:
ifconfig

it should show you your IP address.  If it doesn't show something like '192.168.1.4' or something close, then you may not actually be connected properly.

Are you able to access your router via 
[http://192.168.1.1](http://192.168.1.1)  or 
[http://192.168.2.1](http://192.168.2.1) ? 

Do you have security settings in place (WEP)?  

Do you have MAC address filtering turned on?

---

### Post by htlh on 2006-01-14
Well, then its not a firewall-issue.

All I got after typing "ifconfig" was:
eth1  Link encap:Ethernet  HWaddr 00:0E:35:6C:52:DA
        inet6 addr: fe80:20e:35ff:fe6c:52da/64 Scope:Link
        UP BrOADCAST RUNNING MULITCAST MTU:1500 Metric:1 
        RX packets:500 errors:0 dropped:0 overruns:0 frame:0
        TX packets:51 errors:0 dropped:0 overruns:0 carrier:1
        collisions:0 txquelen:1000
        RX bytes:17208 (16.8 KiB) TX bytes:15468 (15.1 KiB)
        Interrupt:18 Base address:0x4000 Memory:e0206000-e206fff

Ive configured it to get an IP from DHCP.

And no, I dont have a WEP-key or MAC address filtering on.

If it is of any relevancy, the wireless router is connected to a switch, and the switch is in turn connected to the broadband-modem.

---

### Post by BathroomNinja on 2006-01-14
That might be the issue.

It should be:   MODEM ---> ROUTER ----> SWITCH--- > COMPUTERS

However, it looks like you are not connecting to your router at all.  Go into your router and reset the settings, then plug everything in the way shown above. Try again.

---

### Post by htlh on 2006-01-14
Do you mean physically reset the router, like pressing the tiny button saying "reset" on the side/under the wireless router, or do you mean by accessing the "options"-menu somewhere and change the settings there?

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=htlh]Do you mean physically reset the router, like pressing the tiny button saying "reset" on the side/under the wireless router, or do you mean by accessing the "options"-menu somewhere and change the settings there?[/QUOTE]


Either way works fine.

---

