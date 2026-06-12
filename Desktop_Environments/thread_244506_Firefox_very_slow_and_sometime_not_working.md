---
title: "Firefox very slow and sometime not working"
date: 2006-08-26
forum: Desktop Environments
---

### Post by tam on 2006-08-26
Hello
I am very new to the Linux world. I have just installed 6.06 release in a VMWare environment. Apparently everything is fine and working, but for Firefox.
Sometime it takes very long to load pages, sometime it does not even succeed in getting the page and timeout expires.
The parallel firefox on windows XP works very well, so it is not a matter of poor bandwidth.

The PC is linked to te internet through an ADSL router.
My Ubuntu network is configured as DHCP and if I go to the ADSL router admin interface, the Ubuntu user is assigned an IP address.

I have checked another virtual machine, a SuSe virtual PC and that works very well, but the browser in there is Conqueror, not Firefox. I want to use Ubuntu and Firefox.

I've done a traceroute on yahoo.com.
The path stops at: ge-3-1-0-p141.msr1.rel.yahoo.com, 216.115.108.59

Can somebody please help me on this problem?
Thanks in advance.

Regards

---

### Post by kaamos on 2006-08-26
Is there a clear difference when connecting to

1) [http://www.google.com/](http://www.google.com/)
2) [http://72.14.221.104/](http://72.14.221.104/)

?

---

### Post by tam on 2006-08-26
thanks for the help.

Yes there is a difference:

[www.google.com](www.google.com) does not work

the direct IP address work perfectly. 

Sounds like I have a DNS problem, but I would not know what to do now to sort it out?

Thanks again.

---

### Post by kaamos on 2006-08-26
Try this:

1) Type about:config in ff address bar. 
2) in the filter type ipv6
3) change the key network.dns.disableIPv6 to true
4) restart browser

---

### Post by tam on 2006-08-26
thanks a lot.
It is fixed now, great!! and thanks for the help !!!
Just one more question if you do not mind. The WinXP Firefox config has FALSE as the IPv6 value, but it works....
Where is the trick?

Grazie from Milano, Italy.

---

### Post by kaamos on 2006-08-26
I think only the upcoming windows vista has native support for ipv6.

---

