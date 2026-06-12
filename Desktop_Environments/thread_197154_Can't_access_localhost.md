---
title: "Can't access localhost"
date: 2006-06-15
forum: Desktop Environments
---

### Post by JasonMU on 2006-06-15
Hi - I have this problem: when I try [http://localhost](http://localhost), Firefox tells me that
"Firefox can't establish a connection to the server at 127.0.0.1."  I used to not get this, but now I do.  BTW, ping seems to get through.  Do you have any sugggestions for fixing this?

Thanks,

Jason

---

### Post by nanotube on 2006-06-15
that would only work if you are running a webserver on your computer. are you running a webserver? the default install would not have that.

---

### Post by lkagan on 2006-06-15
Sounds like apache simply isn't running.  Try:
```

sudo /etc/init.d/apache2 start

```

If you still can't access apache, it's probably firewall related.  I've noticed that Ubuntu has finally added some rules to iptables in this release.  Unfortunately, I don't know where those rules are.  I wrote an iptables script for my webserver that I setup to start at the proper init levels.  If you like you can simply open up access to everything on your machine when requests come from the localhost.  It should already be set this way.  In any case, I'm giving you my iptables script and you can dissect it for your needs.

```

# Flush any current chains in memory.
iptables -F

# Set the default policy for the INPUT target.
iptables -P INPUT DROP

# Allow inbound traffic for any connections that are related to requests
# originated by this box.
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow all inbound traffic destined ssh
iptables -A INPUT -p tcp --destination-port 22 -j ACCEPT

# Allow all inbound traffic destined to http
iptables -A INPUT -p tcp --destination-port 80 -j ACCEPT

# Allow all inbound traffic from the localhost
iptables -A INPUT -s 127.0.0.1 -j ACCEPT


```

Good luck,

Larry

---

