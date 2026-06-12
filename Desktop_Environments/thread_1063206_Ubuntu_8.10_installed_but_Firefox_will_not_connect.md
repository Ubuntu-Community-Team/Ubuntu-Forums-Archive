---
title: "Ubuntu 8.10 installed but Firefox will not connect"
date: 2009-02-07
forum: Desktop Environments
---

### Post by Tim55555 on 2009-02-07
Hello,
I've just completed a fresh CD install of Ubuntu 8.10 and I have connectivity to the net (i.e., can ping IPs outside my network), but cannot get Firefox 3.0.3 to connect. As well, I can ping other machines on the network as well as the routers. I can even access the routers with Firefox.

I am connecting through 2 routers (wired to wireless) and yes the are dated. I'm using a static IP, gateway (wired router)and dns-nameservers (wireless router) all defined in /etc/networks/interfaces.

I've disable ipv6 in Firefox about:config as well as added ipv6 to the blacklist.

I'm close to turfing Ubuntu and letting the dog play with the CD as a frisbee.

My frustration is caused by knowing I'm close, but I cannot find that last setting.

Please help. Sincerely, Tim.

---

### Post by gettinoriginal on 2009-02-07
Have you done Edit > Preferences > Advanced > Networking > Configure how Firefox connects to the internet ?

---

### Post by Tim55555 on 2009-02-07
Thanks for the reply. Yes, tried all but "manual proxy config" and "auto proxy config URL" as I didn't know what to use. Made some guessess, but no go. I assumed that "use system proxy settings" was correct because of the second router as DNS? 

As I sit and cuss at that monitor, it seems odd to me it times out immediately. Ring any bells?

---

### Post by gettinoriginal on 2009-02-08
Clear all your cookies and cache, set to "use proxy settings", close firefox, and reopen.

---

### Post by Tim55555 on 2009-02-08
I first cleared all cookies (there was none) and privacy data just in case. Sorry, but Firefox 3.0.3 has no "use proxy settings," but I assumed you mean "auto-detect proxy ..." Just in case, I also tried "use system . . " and "no proxy." Still no connection. I should tell you that I have Debian file server on my home network running Apache for intranet and Firefox views that page fine.

---

### Post by Tim55555 on 2009-02-08
Eureka!! Found the solution posted here by marcobra.

[https://answers.launchpad.net/ubuntu/+question/52187](https://answers.launchpad.net/ubuntu/+question/52187)

Edited /etc/resolv.conf with a nameserver entry with the ip of my DNS (wireless router).

Thanks very much for your time gettinoriginal.

---

### Post by gettinoriginal on 2009-02-08
Glad it's fixed :p

---

