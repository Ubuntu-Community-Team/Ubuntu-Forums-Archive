---
title: "basic dns tunneling question"
date: 2009-06-07
forum: General Help
---

### Post by meg23 on 2009-06-07
I am try to set up dns tunneling but I do not understand the nameserver directions. 

"If you just have a DynDNS account and no static IP, you'd set up the delegation using a CNAME record. As mentioned above, CNAME is a canonical name (speak: an alias). So when a server gets back a CNAME instead of an A record (IP address) he continues to look up this hostname. That brings us to the following:

sub.example.com.              IN      NS      ns.extern.example.com.
ns.extern.example.com.        IN      CNAME   foo.bar.dyndns.org."

I do have dyndns.com server already. Can anyone explain to me what I need to do?

---

