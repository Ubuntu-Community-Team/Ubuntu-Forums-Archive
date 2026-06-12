---
title: "Can't Download Updates"
date: 2006-07-22
forum: Desktop Environments
---

### Post by SuperMike on 2006-07-22
Did an 'apt-get update' today and it says Connecting to us.archive.ubuntu.com, but can't get there. When I try to ping, it comes back okay. When I try to do a whois on the IP address of it or the name of it, it always come back with "Argonne National Laboratory"??

I'm very skilled with /etc/apt/sources.list and know that this is correct. I'm using the default Dapper one.

I'm on Verizon DSL. Something might be screwed up with their DNS.

I tried dropping and reconnecting, but I get the same problem.

Perhaps some malicious hacker is messing with the DNS routers again?

I waited several hours and I get the same problem.

The fix for now is to switch from 'us' to 'uk' in the /etc/apt/sources.list for this line, but the problem with that is that I might end up with UK type dictionary stuff if it ever needs to update that.

---

### Post by taurus on 2006-07-22
If you have followed it the last hour or so, us.archive.ubuntu.com is down so you can either wait until tomorrow to update your machine or remove the "us" in front of those lines and try it...

---

### Post by SuperMike on 2006-07-23
They had a power outage that affected both ubuntuforums.org and ubuntu.com. Probably has to do with the extremely hot worldwide temperatures. Everything's back up now.

---

