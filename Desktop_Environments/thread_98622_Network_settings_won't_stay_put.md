---
title: "Network settings won't stay put"
date: 2005-12-03
forum: Desktop Environments
---

### Post by JimMartin on 2005-12-03
Hello All:

I have a small but annoying problem with Ubuntu.
Each time I reboot, my network settings change. Upon reboot they are always:
DNS Servers:  192.xxx.x.x  and 198.xx.xx.x
and
Search Domains:  domain.actdsltmp

With these settings, my internet access is badly compromised or completely lost.  The folks at my IP, Xmission, all use Ubuntu and instructed me to change one of those DNS server settings and to delete the search domain. When I make those changes internet performance is great. 

But no matter what I do the settings revert on reboot. And yes, I have checked the "save current setup" box when I restart.  

Anyone wanna give me a solution?  Its not a huge deal to reset them every time but I'd sure like to fix the problem.

Thanks in advance,

Jim

PS: Under the connection settings:
Configuration is DHCP
IP address is blank
Subnet mask is blank
Gateway address is blank

---

### Post by Qrk on 2005-12-03
I'd recommend

```
sudo gedit /etc/resolv.conf
```

You should be able to make the changes there. Depending on your service, the format can be different, but it looks like replacing it with this will work:
```

#search domain.actdsltmp
nameserver (New DNS)
nameserver 198.xx.xx.x
```

Edit: Be sure to make a copy of what was there before.

---

### Post by JimMartin on 2005-12-03
Forgot to mention that I had done that. That was one of the fixes proposed by the guys at XMission but it dosen't do the trick. 

Any other ideas?

Thanks,

Jim

[QUOTE=Qrk]I'd recommend

```
sudo gedit /etc/resolv.conf
```

You should be able to make the changes there. Depending on your service, the format can be different, but it looks like replacing it with this will work:
```

#search domain.actdsltmp
nameserver (New DNS)
nameserver 198.xx.xx.x
```[/QUOTE]

---

### Post by DrBair on 2005-12-03
Still, everytime he reboots its going to poll for new settings.  

If you're connected via a router or if you have a static IP you could just manually set all the stuff and be done with it. Otherwise I suppose you could write a post-up script to automate the settings changes for you.

---

### Post by JimMartin on 2005-12-04
if you have a static IP you could just manually set all the stuff and be done with it. 

Thanks for the tip. I obtained all the static IP settings and it works like a charm.

Cheers,

Jim

---

### Post by Koobi on 2005-12-04
[QUOTE=DrBair]
If you're connected via a router or if you have a static IP you could just manually set all the stuff and be done with it. Otherwise I suppose you could write a post-up script to automate the settings changes for you.[/QUOTE]


i have the same problem.

currently, i do this everytime my PC starts up:
```

sudo cp /etc/resolv.conf.bak /etc/resolv.conf

```

does anyone know how i can automate this? i'm not familiar with perl or python or shell scripting. all i know is PHP so some help would be appreciated.


thanks

---

