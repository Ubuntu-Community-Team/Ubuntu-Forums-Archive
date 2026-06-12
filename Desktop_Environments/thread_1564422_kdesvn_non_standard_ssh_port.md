---
title: "kdesvn non standard ssh port"
date: 2010-08-30
forum: Desktop Environments
---

### Post by infinitezero on 2010-08-30
Does anyone know what I need to add to the .ssh/config file to use kdesvn on a repo with non standard ssh port?

I have added the following, but still no joy.

Host <hostname.tld>
	Port <portnumber>


Thanks,
iz

Never mind, answered my own question:

HostName <ipaddress>
          Port <port#>
          User <yourusername>

---

