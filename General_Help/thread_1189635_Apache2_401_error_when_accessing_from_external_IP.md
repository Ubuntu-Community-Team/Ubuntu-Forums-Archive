---
title: "Apache2 401 error when accessing from external IP"
date: 2009-06-16
forum: General Help
---

### Post by gordonsowner on 2009-06-16
Hi,

I'm running Apache 2.2.8 on Ubuntu 8.04.  I recently enabled my DSL modem and linksys router to do port forwarding.  This is working fine for ssh to the public IP I have.

Now I am trying to make Apache2 work.  I have a little test index.htm file that I can get with my browser when I type in [http://localhost](http://localhost), but when I try to do the same thing with http://<public IP>, I get challenged with a username/password popup, which I can't seem to find the right combination for, and then I get a 401 error.  Any ideas why I can get it to work locally, but not from an external access?

Thanks,

---

### Post by Hobgoblin on 2009-06-17
Have you forwarded port 80?

I am guessing that what you are getting is your router's web management interface.  Is it set up to allow access from the WAN to the web interface?  Was the router supplied by your ISP?  In some cases the ISP has the web interface open from teh WAN to do their own maintenance.

---

### Post by gordonsowner on 2009-06-17
Hi,

I have forwarded port 80 with the same method in which I forwarded port 22 for ssh (which does work).

I'll check on whether or not the router (which was supplied by my ISP -- Qwest, with an Actiontec GT701).  My recollection was that it was turned off, but I will check again when I get back home.

Thanks for your response,
Matt

---

