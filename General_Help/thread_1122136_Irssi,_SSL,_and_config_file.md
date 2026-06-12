---
title: "Irssi, SSL, and config file"
date: 2009-04-10
forum: General Help
---

### Post by khoma on 2009-04-10
Hi

I was wondering if anyone could tell me how to edit the irssi config file to autoconnect to a server using SSL?

Thanks )

---

### Post by Grognot on 2009-04-10
open up the config file, look for the server you want ssl enabled on and add use_ssl = "yes"; to the end. Example:
```

servers = (
  {
    address = "irc.quakenet.org";
    chatnet = "QuakeNet";
    port = [color=red]"6667";[/color]
    autoconnect = "yes";
    [color=red]use_ssl = "yes";[/color]
  }
);
```
The red bits are the important parts, i.e. use the right port.

---

