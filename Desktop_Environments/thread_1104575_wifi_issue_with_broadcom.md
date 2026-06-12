---
title: "wifi issue with broadcom"
date: 2009-03-23
forum: Desktop Environments
---

### Post by daboroe on 2009-03-23
output of lspci
```

02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

I am aware of this bug
[Complete system freeze when trying to connect to WPA2 network]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305907")

They said they think they found a fix. For a person it did work. 

I am trying to follow this information

It works until 
```

insmod <path>/wl.ko

```

it says file already exists. I am lost after that as well as the actual patch. 

Any help would be great and well appreciated.

---

### Post by daboroe on 2009-03-24
bump

---

