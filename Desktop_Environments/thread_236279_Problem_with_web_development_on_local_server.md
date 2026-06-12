---
title: "Problem with web development on local server"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jlhughes on 2006-08-14
Here's the setup:

I have Ubuntu with a LAMP server running on a local machine with a fixed internal network IP address.  

This machine is connected to the Internet through a router. The WAN side of the router has a fixed IP address. 

I have three domain names that point to the router's fixed IP address. The router sends all Web traffic to the Ubuntu LAMP server.  The Apache virtual hosts directive sends the Web requests to the appropriate local directory.

This all works great.

Now the problem: 

I do web development on the same Ubuntu box on Web sites that are associated with the domain names pointing to the fixed IP address and eventually to a specific local directory.  When I use a web browser to visit one of these domains, the browser will often hang. Stopping and restarting the page loading will "fix" this, but it doesn't always help.

I'm assuming (I'm not an expert in any of this) that the router is confused by the routing of internal IP traffic asking for an outside IP that is actually internal traffic. (At least I'm confused.) 

I can't just set the browser Web address to the local file or the machine's internal IP address because the Web sites have pages that want to load based on the domain name URL. In other words, if I want to test what outside people will see I must use the outside address.

Would modifying the hosts file to point all traffic to a specific domain to a specific local folder work? If so, what would an example entry look like?

Or is there some other solution?

---

### Post by karih on 2006-08-14
> **jlhughes said:**
> Would modifying the hosts file to point all traffic to a specific domain to a specific local folder work? If so, what would an example entry look like?Yes, I belive so.

You could add below the 127.0.0.1 entries somthing like this:
```
1.2.3.4 domain.tld
```
And then all requests to domain.tld would be redirected to 1.2.3.4

Hope this helps!

---

### Post by Uluen on 2006-08-14
You can't use folders in the hosts file, only network/address.

But this does sounds like a DNS issue to me.

Update the hosts file on your development box to read
1.2.3.4    domain1.net
1.2.3.7    subdomain.domain1.net

Apache will direct vhost traffic to the correct domains.

---

### Post by jlhughes on 2006-08-15
Thanks for the help. This appears to have done the trick!

---

