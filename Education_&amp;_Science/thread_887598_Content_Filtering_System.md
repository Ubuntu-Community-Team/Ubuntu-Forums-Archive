---
title: "Content Filtering System"
date: 2008-08-12
forum: Education &amp; Science
---

### Post by Motorh3ad on 2008-08-12
I am a computer technician for a school district. We are currently planning on changing over to a privatized network topology. 

One of the things I have been charged with is finding a internet content filtering system for each site. 

Being a huge fan of Ubuntu servers this is the first place I wanted to check. 

Does anyone know of an open source content filtering app that will run on ubuntu?

We would preferably like it to have accounts... do be used to bypass filtering per IP address.

---

### Post by hubie on 2008-08-22
I'm not sure about the multiple accounts, but it sounds like you want a squid proxy with filtering.  [This site]("http://www.linux.com/feature/60050") looks like a good place to start.

---

### Post by torry_loon on 2008-08-22
I agree with hubie. You can use squid as a proxy server with SquidGuard or Dan's Guardian as the filter.

If you use the ident service on the client machines (I have found that pidentd works best on ubuntu), it will translate the IP address of the machine into the current username so you can filter by username.

---

