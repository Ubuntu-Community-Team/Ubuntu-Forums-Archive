---
title: "Not wanted connections"
date: 2009-06-17
forum: General Help
---

### Post by Peque on 2009-06-17
Hey Guys. 

I've discovered today through a netstat -ta some issues that I would to getting explained. In the netstat -ta output: 
```

tcp        0      0 172.16.50.10:59447      undernet.xs4all.nl:ircd ESTABLISHED
tcp        0      0 172.16.50.10:47123      zagreb.hr.eu.under:ircd ESTABLISHED
tcp        0      0 172.16.50.10:36791      undernet.xs4all.nl:ircd ESTABLISHED

```
I have no IRCU IRCD installed and haven't use anything like this - so what cdould this be!
Funny enough a cat services | grep ircd shows this: 
ircd		6667/tcp			# Internet Relay Chat

But have not installed anything else but Bind9 and apache2! 

What can I do about this?

---

