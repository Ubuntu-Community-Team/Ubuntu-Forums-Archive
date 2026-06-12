---
title: "Slow Browsing"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Derspankster on 2006-09-26
I'm generally happy with Ubuntu 6.06 with the exception of browsing speed. I've already disabled IPV6 globally, have Fasterfox installed, the latest Firefox installed etc.  But, the net just crawls. I'm on a 5000kb network connection but it takes forever to resolve pages compared to my Windows boxes. Not sure what to try next. This keeps me from using Ubuntu more than I do. The Linux computer is a 1 GB with 512 mb of ram. My speed tests on the Linux computer are very good but browsing is very slow.

---

### Post by wieman01 on 2006-09-26
Disable "ipv6" in Firefox as well:

1. URL: "about:config" then <enter>.
2. Search for "ipv6" (use the Filter).
3. Right-click on "network.dns.disableIPv6" and select "Toggle".

That's it. Please try again.

---

### Post by Derspankster on 2006-09-26
Thanks for the reply but I already did that

---

### Post by wieman01 on 2006-09-26
Are both router & wireless network device running on the same bit-rate (e.g. 54 MBit)?

---

### Post by Derspankster on 2006-09-26
This machine is cabled to my router

---

### Post by dca on 2006-09-27
That's too bad, I too have that same problem...  Solving the issue should be paramount.  I know a lot of enterprises where over half their systems (POS, inventory, shipping, etc) are web-based...  Darn memory leakage...

---

### Post by Derspankster on 2006-09-27
I'll tell you this, if I can figure it out, I'll surely post the fix here. I've read everything I could find on this but can't resolve it. I appreciate everyone's input. This is a great forum.

---

### Post by wieman01 on 2006-09-27
Another thought is to use a DNS other than the one that your service provider assigns to you. If have seen similar posts and people could get around the performance issue by replacing the default DNS.

Do you know how to do that? If not, then I can help you. Simply let me know if you're using DHCP or Static IP.

---

### Post by Derspankster on 2006-09-27
I'm using DHCP.

---

### Post by wieman01 on 2006-09-28
The why not try Static IP and see if the performance gets any better when replacing the DNS? I would give it a shot since you run out of options anyway...

---

### Post by Derspankster on 2006-09-28
Took your suggestion and switched to a static IP. It has helped some. I'll keep an eye on performance. Thanks.

---

### Post by wieman01 on 2006-09-28
Ok... Try to replace the DNS. Perhaps that's your problem.

---

### Post by Derspankster on 2006-09-28
Not sure what you're saying. Sorry.

---

### Post by wieman01 on 2006-09-28
Ok... Could you post this file? Then I'll explain it to you... No problem.
> gedit /etc/network/interfaces

---

### Post by Derspankster on 2006-09-28
OK, here goes.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.240
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by wieman01 on 2006-09-28
Ok, now open "interfaces" with super-user:
```
sudo gedit /etc/network/interfaces
```
Then paste this (I deliberately deleted the stuff that you don't need - it's safe to do that):
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.1.240
    netmask 255.255.255.0
    [COLOR="Red"]network 192.168.1.0[/COLOR]
    [COLOR="Red"]broadcast 192.168.1.255[/COLOR]
    gateway 192.168.1.1
    [COLOR="Red"]dns-nameservers 192.168.1.1[/COLOR]
```
I have also added a few lines (in red).

Now restart the network & try to browse the web:
```
sudo /etc/init.d/networking restart
```
If this does not help, we'll try another name-server (DNS).

Please make a safety copy of the file before you make any changes to it. This way you can restore your settings anytime.

---

### Post by wieman01 on 2006-09-28
If the performance is still poor, then replace dns-nameserver with this:
> [COLOR="Red"]dns-nameservers 208.67.222.222[/COLOR]
The restart the network (or reboot) and try! This is an open DNS that was referred to in one of the threads.

---

### Post by Derspankster on 2006-09-28
The static IP has helped quite a bit. Once I get to a domain, all pages load rather quickly, it's still pretty slow getting there. Not sure that made sense.  I haven't tried replacing the DNS. I appreciate your help. You might have guessed that I'm not that well versed in Linux.

---

### Post by wieman01 on 2006-09-28
> **Derspankster said:**
> The static IP has helped quite a bit. Once I get to a domain, all pages load rather quickly, it's still pretty slow getting there. Not sure that made sense.  I haven't tried replacing the DNS. I appreciate your help. You might have guessed that I'm not that well versed in Linux.
Don't worry... Take your time. I have been through this myself. :-)

Also try replacing the DNS with the address I have given you. Then reboot(!) the computer and see if it gets any faster. This should definitely help.

---

### Post by Derspankster on 2006-09-30
I made the changes you mentioned and things have definitely improved. I've not tried changing dns nameservers. While the performance boost is substancial, it still doesn't quite match my Win boxes. However, it's not that bad at all. Thank you again for your help.

---

### Post by wieman01 on 2006-09-30
> **Derspankster said:**
> I made the changes you mentioned and things have definitely improved. I've not tried changing dns nameservers. While the performance boost is substancial, it still doesn't quite match my Win boxes. However, it's not that bad at all. Thank you again for your help.
Alright. I have seen similar staff in the forum and was really wondering the root cause... Still scratching my head. But I figured that Linux lags behind Windows as far as wireless & wireless security are concerned. It hurts to admit that but it's a simple truth.

And kernel updates are a killer... Anyway, glad it helped.

---

### Post by Derspankster on 2006-09-30
I haven't tried Linux wireless. My Ubuntu computer is wired. Kind of had a scare while I was fooling with the network settings. I've been an Adelphia customer and I was migrated to RoadRunner right in the middle of my "adjustments" Lost all connectivity but realized what had happened. Rebooted my modem and router and all is well again. I'm now a roadrunner customer. At any rate, my browsing speed has improved. Thanks again.

---

### Post by Derspankster on 2006-10-08
Finally has solved my browsing speed issue! Somehow, I had two different ethernet profiles and they were different. Also, I must have mistakenly entered my print server as a DNS host (along with the correct one) At any rate, I deleted the print server host, eliminated the extra profile, set a fixed IP and now I'm flying! Thanks to all for their excellent responses.

---

### Post by Derspankster on 2006-11-16
I've been asked to summarize my steps for improving my internet browsing. I'll try to keep this short and to the point.  I should point out that I'm running Dapper and have manually installed Firefox 2.  Here are the changes that I've made.

1. Disabled IPV6 in Firefox
2. Disabled IPV6 globally
3. Enabled a static IP rather than using DHCP (router is a Linksys) and I am cabled, not wireless)
4. Eliminated a duplicate network profile for my Ethernet card.
5. Moved to OpenDNS rather using my ISP's DNS. Instructions are [here]("http://www.opendns.com/").

My Linux computer is now at least as fast browsing the net as my Windows boxes. If you are unsure on how to do some of these things, just query this forum and you'll find the information. I won't copy it here. Hope this helps those having similar issues.

---

