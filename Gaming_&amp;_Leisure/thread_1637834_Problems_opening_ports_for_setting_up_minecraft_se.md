---
title: "Problems opening ports for setting up minecraft server"
date: 2010-12-05
forum: Gaming &amp; Leisure
---

### Post by herteljt on 2010-12-05
Hi all,

I've been trying to setup a minecraft server on my home machine. My problem is getting the port 25565 to open.

Here is what I have done so far:
- I have enable the port forwarding in my router.
- I tried opening the port using ufw (did not work)
- I created a script and disabled iptables as noted here [ https://help.ubuntu.com/community/IptablesHowTo#Disabling the firewall ]( https://help.ubuntu.com/community/IptablesHowTo#Disabling the firewall ) (did not work)


I have been checking using [ http://www.canyouseeme.org/ ]( http://www.canyouseeme.org/ )

Oddly enough when I listen using netcat
```
netcat -l 25565 
```

Then I am able to connect to the port.

Could someone help me out?

---

### Post by .kelp on 2010-12-05
You could use Hamachi if everything else fails.

---

### Post by herteljt on 2010-12-05
> **.kelp said:**
> You could use Hamachi if everything else fails.


Thanks for the suggestion, but I would like to be able to handle this without installing more software if possible.

I have been trying ufw and gufw and in each case I can create a rule that opens the port, but I am unable to connect from an exterior site.

Edit: 

I have found a messy but useable workaround.

I start netcat using the -l and -k options (-k makes it repeatedly open the port). Then I ctrl-z the operation (to put it in the background). Then I kill the process. For some reason this leaves the port open.

```
netcat -l -k 25565 
```

---

### Post by herteljt on 2010-12-08
Woot! I think I have figured out my problem.

After a bit of reading on the forums I discovered that forwarding the port is not enough you must also make sure something is listening to the port.

For some reason the Minecraft server is not listening so I used netcat to listen as described here [url] 
http://www.jfranken.de/homepages/johannes/vortraege/netcat_inhalt.en.html [/url]

I made a simple little script

```

#!/bin/bash

# Run server and have netcat listen on port 25565
java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui | netcat -l -p 25565


```

I hope this helps someone else who encounters the same problem.

---

