---
title: "DNS will not flush"
date: 2009-06-13
forum: General Help
---

### Post by sistarbliss on 2009-06-13
I have a question about the best way to completely clear cache in linux. 
 
Installed wordpress in a subdir, set dns, waited some time, till the nameservers were set, pinged domain --pinged fine to new hosting provider. Logged into CP on new server, and noticed announcement that the domain had expired. I was like *what the heck?!?* So I contacted onandone (registrar & previous host) to ask about it. They said that it was set to autorenew. Well, from what bluehost told me (new hosting provider) the domain had expired and was re-registered. Unfortunately, this was right about the time when I set the WP to point to the original domain instead of the subdir. 
 
Now when I go to the domain, it's displaying the cached version and when I ping it from linux it points to oneandone. When I do all of this from windows, everything works fine. I've cleared my firefox cache, and also did /etc/init.d/dns-clean start, and rebooted my system. I can't even point to the subfolder anymore. When I try to access the domain via mydomain.com/subfolder.com It renders as pure text, and when I try to access the wp-admin from mydomain.com/subfolder.com I get a oneandone 404 page. 
 
Anyone here ever experienced this?  I'm stumped.

I also did installed nscd then did /etc/init.d/nscd restart, and sudo network restart to no avail.  An help would be greatly appreciated. I'm running  64 bit jaunty.

---

### Post by statistic on 2009-06-13
You can try 

/etc/init.d/dns-clean restart

I'm not sure if that actually works, but how to clear dns cache would be relevant to my interests as well because of all dns-changing my awful router does.

EDIT: sorry, just saw you did that.

---

### Post by lamego on 2009-06-13
Linux does not perform DNS caching, if when you ping/nslookup the terminal you are getting the old IP address, it means that is the information on name server configured on your /etc/resolv.conf .

---

### Post by sistarbliss on 2009-06-13
> **lamego said:**
> Linux does not perform DNS caching, if when you ping/nslookup the terminal you are getting the old IP address, it means that is the information on name server configured on your /etc/resolv.conf .

How would I reset this?

---

### Post by sistarbliss on 2009-06-13
I changed network settings to point to local dns server instead of isp's, and that has resolved my issue.

---

### Post by statistic on 2009-06-13
> **lamego said:**
> Linux does not perform DNS caching, if when you ping/nslookup the terminal you are getting the old IP address, it means that is the information on name server configured on your /etc/resolv.conf .

Aahh thank you, this actually helped solve my problem. It gets it's information to do the dns changing from my resolv.conf, so I just removed the line that pointed to that gateway.
No more wsearch crap! Yay!

---

### Post by Ebere on 2010-04-16
> **sistarbliss said:**
> I changed network settings to point to local dns server instead of isp's, and that has resolved my issue.

How did you do that ?

I am using Kubuntu.

---

