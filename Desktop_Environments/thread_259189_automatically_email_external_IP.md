---
title: "automatically email external IP"
date: 2006-09-17
forum: Desktop Environments
---

### Post by stewacide on 2006-09-17
Really simply question: what is the easiest way to have my home linux 
server email me its external IP whenever it changes / on an interval, 
so I can connect to it remotely? (I have a Ubuntu file server at home, 
which I want to connect to when I'm off at school: it's a dynamic IP of 
course). 

A web service that did this (kept track of the IP) would work as well. 

I'm a relative Linux n00b (my other computer is a Mac ;)), so I'd prefer 
a program or service that did this, not to have to run some kind of 
script but if that's what I have to do so be it... 

I can't seem to turn up anything simple on Google. 

[COLOR="Red"]Thanx in advance![/COLOR]

---

### Post by sktx on 2006-09-17
check out [http://www.dyndns.org](http://www.dyndns.org) or you might have a little luck searching google for "dynamic dns"

sorry i couldn't be of more help.

  sktx

---

### Post by Zyzzyx on 2006-09-17
Yeah, I'd recommend DynDns as well. I have my domain set up through them, and software running that checks for IP changes, then sends the new IP to their servers, registering the new IP in my DNS entries. Now, this is on my Windows Server 2003 system, but it looks like there's similar programs available for Linux as well.

[http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)

Hit that (while in Linux, it changes by OS), and should list two to start with, and then there's a 'third party clients' page as well. I would think that you could run these programs *without* having to sign up with DynDns.


edit add: just checked the client on my Win2K3 system, it has an 'email on IP change' option, so should be available on others as well.

---

### Post by karamba_kid on 2006-09-17
Like the last post said dyndns or another similar dynamic dns service is what your looking for.  You will usually set that up in your router's configuration.  Here you can checkout the latest episode (#152) of this podcast... [http://twatech.org/](http://twatech.org/) for some more info. Personally I haven't listened to this episode, but the title is Dynamic DNS so it could be of some help. Good-luck :-D

---

### Post by mssever on 2006-09-17
I just looked at DynDNS; for some reason, I thought it was a paid service, but apparently not. For the sake of completeness, here's what I've done:
Set up a remote website that records the IPs of the client requesting certain URL. Then, I set up a cron job to send a wget request. But, I think that DynDNS is a simpler solution.

---

### Post by Zyzzyx on 2006-09-17
Depending on what you want/need, DynDNS can be free, or paid. I'm using the paid service, as I also have my mail going through them, since my mail server is on the same dynamic IP. I've had friends use the free side of their services just fine though.

And as mentioned, if you just want change of IP notification, probably don't even have to mess with DynDNS, just check out the clients they have listed. Now, if you want to have some kind of domain name instead of just an IP, then yeah, go through DynDNS. Sounds like for what you're doing though, plain IP is fine.

---

### Post by stewacide on 2006-09-17
Thanks a lot for the DynDNS link. That should work very well. I'm going to see if my router supports it because that would be ideal.

---

### Post by stewacide on 2006-09-17
The router update seems flakey. Any recommendations on a Linux client?

---

### Post by karamba_kid on 2006-09-18
> **stewacide said:**
> The router update seems flakey. Any recommendations on a Linux client?

My router runs Linux. ;) 

(Sorry I just had to let the world know)

---

