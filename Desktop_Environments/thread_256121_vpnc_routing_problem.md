---
title: "vpnc routing problem"
date: 2006-09-12
forum: Desktop Environments
---

### Post by dallingham on 2006-09-12
I am using vpnc to connect into work from home. For the most part, it is working. However, all traffic is getting routed to work, instead of just the desired addresses. I have tried adding the "Target networks" option to my configuration file, but this produces an error. The line I add is:

Target networks XX.XX.XX.0/255

where the XX.XX.XX.0 are the actual subnet I want to route. This is straight from the vpnc man page. However, I get an odd error message:

Error: an inet prefix is expected rather than "XX.XX.XX.0/255"

(No, I am not using XX, but real and valid numbers)

Any ideas on what is wrong? The whole default.conf file is:

IPSec gateway YY.YY.YY.YY
IPSec ID **********
IPSec secret **********
Xauth username ***********
Xauth password ***********
Target networks XX.XX.XX.0/255

Without the Target networks line, everything works, but all traffic is routed through the vpn.

---

### Post by mkgs on 2007-06-14
If you still have this problem, here is a fix which works for me 

Uncomment the following line in your configuration file - 

DNSUpdate no

and do not specify any target networks.

---

### Post by huotte on 2008-03-17
This is an old thread, but I'll post a reply anyway just in case someone else with the same question stumbles upon it.

The format of the argument to the Target networks line is incorrect. The number after the slash should be the number of bits in the netmask of the network you are connecting to. For example, if your target network uses a netmask of 255.255.255.0, then the entry should look like this:

Target networks XX.XX.XX.0/24

With a netmask of 255.255.0.0, the format of the line would be:

Target networks XX.XX.0.0/16

and so on.

---

