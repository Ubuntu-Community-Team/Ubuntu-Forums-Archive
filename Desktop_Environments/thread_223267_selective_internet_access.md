---
title: "selective internet access"
date: 2006-07-26
forum: Desktop Environments
---

### Post by roneilden on 2006-07-26
Newbee to Linux and Ubuntu seeking assistance. Having dapper now up and running I can only access certain sites. As an example, Firefox will take me to Mozilla Store (takes about 20 seconds to load with 256k ADSL) but when going to MozillaZine, I get the 'Unable to connect, problem loading page'. Same with Google, I can access 219.90.238.32 but not Google Australia.

The DNS servers appear to be set correctly in /etc/resolv.conf with

search 203.2.124.164 203.2.124.165
nameserver 192.168.1.1
nameserver 203.2.124.164
nameserver 203.2.124.165

I don't know what else to check and would appreciate any ideas

Peter

---

### Post by OpsVentus on 2006-07-26
You can try to move down 'nameserver 192.168.1.1' so the dns-servers of your ISP will be at the top, thus using those and not your router.

Cheers,
Bart.

---

### Post by roneilden on 2006-07-26
Hi Bart,

That worked very well, everything was fast and fine until I rebooted and the machine defaulted back to the router. Is there a way I can save the /etc/resolv.config file so it remains the same on boot up or should I turn off DHCP and manually set it up for the ISP address.

Thanks again

Peter

---

### Post by OpsVentus on 2006-07-26
If you use DHCP it will properly want back to these settings, but you can try to set the dns in the network-manager.
Not sure if it works.
Else, use static ip.

Cheers,
Bart.

---

