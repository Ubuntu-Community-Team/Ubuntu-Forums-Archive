---
title: "Internet has Realy slowed down in the past few days."
date: 2006-09-18
forum: Desktop Environments
---

### Post by captainstormy on 2006-09-18
Ive been using this same install of Dapper since it was available for download.  I havnt had any internet related problems at all untill now.  The Internet has just gotten really really slow in the past couple of days.  Not all the time, just when I first go to a new site.  Like for example, when I first went to come to the forums here it took about 15 seconds for FF to load the page, but to go between threads it is as fast as normal.

Ive tried IPV6 as both enabled and disabled and neither one has helped.  Ive used diffrent web browswers and gotten the same result.

There is a router hooked up, but the net is not slow on any of the other machines using the router, nor is it slow on this machine when I boot into windows.

I could really use some advice on what to do about this.

---

### Post by wieman01 on 2006-09-19
Did you install a firewall (e.g. Firestarter) recently to begin with?

---

### Post by nullmind on 2006-09-19
Sounds like something might be up with your DNS. I noticed that clearing my DNS server and aquiring a new one helped. If your using the default networking you can go to System->Administration->Networking and click the tabs about DNS

---

### Post by subiet on 2006-09-19
> **nullmind said:**
> Sounds like something might be up with your DNS. I noticed that clearing my DNS server and aquiring a new one helped. If your using the default networking you can go to System->Administration->Networking and click the tabs about DNS

had that been the case, his net access from windows should have been slow too, coz most probably he is using the same dns server.

In any case i have always preferred to use an open dns server instead of my isp's. it is generally better, though i think it is not a dns problem, neway here is an open dns address, might just help 
"208.67.222.222"

---

### Post by nullmind on 2006-09-19
Windows does renew it's DNS more often, I noticed my DNS wasn't updated when I reconnected every time. If a the ISP has a DNS load-balancing mechanism, this wouldn't have been working.

---

### Post by captainstormy on 2006-09-19
> **subiet said:**
> had that been the case, his net access from windows should have been slow too, coz most probably he is using the same dns server.

In any case i have always preferred to use an open dns server instead of my isp's. it is generally better, though i think it is not a dns problem, neway here is an open dns address, might just help 
"208.67.222.222"

Using this DNS seems to fix the problem, but It dosn't save it when I reboot I have to type it in each time.  Is there some way to set it automatically at bootup?

---

### Post by wieman01 on 2006-09-20
Yes, by editing the following file in the "interfaces" file right under your wireless device:
> sudo gedit /etc/network/interfaces
Add:
> auto ath0
iface ath0 inet dhcp
[COLOR="Red"]dns-nameservers 208.67.222.222[/COLOR]
"ath0" stands for your own wireless device. Search for your network alias and add "dns-nameservers" beneath it.

---

### Post by GQed76 on 2006-09-20
I've noticed the same behavior, i disabled ipv6 but to no avail.  just seems to take forever to find the site...once you are there, its fine

---

### Post by editrix on 2006-09-21
> **GQed76 said:**
> I've noticed the same behavior, i disabled ipv6 but to no avail.  just seems to take forever to find the site...once you are there, its fine

Same here, and I'm on dialup.

---

### Post by captainstormy on 2006-09-21
> **wieman01 said:**
> Yes, by editing the following file in the "interfaces" file right under your wireless device:

Add:

"ath0" stands for your own wireless device. Search for your network alias and add "dns-nameservers" beneath it.

Thanks for the advice, that didnt seem to help thou.  For now Ive just disconnected the router and hooked my PC up to the cable modem.  It saves the DNS I type in just fine then.

---

### Post by wieman01 on 2006-09-21
Again... Are you using a firewall (e.g. Firestarter) or something like that? This can cause an issue with your DNS settings. You need to "allow" the corresponding ports for DNS to work correctly.

---

### Post by captainstormy on 2006-09-21
> **wieman01 said:**
> Again... Are you using a firewall (e.g. Firestarter) or something like that? This can cause an issue with your DNS settings. You need to "allow" the corresponding ports for DNS to work correctly.

Nope, no firewalls on the linux setup.

---

### Post by GQed76 on 2006-09-26
no firewall here, still slow and clunky resolving addresses

---

### Post by captainstormy on 2006-09-26
Mines acctually gone back to normal now.  :-k

---

### Post by wieman01 on 2006-09-26
> **GQed76 said:**
> no firewall here, still slow and clunky resolving addresses
Do you have a problem with Internet addresses? If that's the case, you're problem may be "ipv6" which you have to disable in Ubuntu & Firefox. Could that be? Had the same issue months ago when I upgraded to Dapper.

---

