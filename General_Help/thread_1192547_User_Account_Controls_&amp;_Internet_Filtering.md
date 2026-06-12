---
title: "User Account Controls &amp; Internet Filtering"
date: 2009-06-20
forum: General Help
---

### Post by umechanism on 2009-06-20
My kids that want to use my computer but I have been reluctant to because I can not find a way to restrict internet access to some sites and there are no user account controls in Ubuntu (like Windows) that keeps up with their activities.

Does anyone know how to setup user account controls and restrict access to some internet sites with Ubuntu 8.10?

Thanks.

---

### Post by dirtrider1 on 2011-07-29
I know this is old but I will reply in regard's to possible new user's with a comparable issue that they need help with. There are actually many solutions provided in Linux. First you can filter at the browser level using browser addons like Foxfilter etc. But this approach can usually be bypassed much easier.Another easy alternative is to filter content based on DNS check out opendns.com and set up a free account and follow the online instructions to set it up with your router. This will filter all content on the entire LAN if set up correctly and the web interface allows you to block entire categories or individual sites based on your preference. Also it is possible to set up a proxy on your home network and filter content and do a few other tasks as well this is probably the most thorough technique check out Dansguardian,Safesquid or Privoxy but all these require a bit of setting up. There are other tools as well like gnomenanny and webcleaner you may wan't to check out as well. And dont forget most routers allow at least a basic level of site filtering and you could always make your own list and use IPtables or put them in /etc/hosts with a loopback address.

---

