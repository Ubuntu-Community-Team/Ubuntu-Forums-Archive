---
title: "cairo dock wifi applet problem"
date: 2009-12-11
forum: Desktop Environments
---

### Post by Docaltmed on 2009-12-11
The cairo-dock wifi applet wants to get its data from eth2, but on my system, eth2 isn't where my wifi is.

I may have a bad case of stupid right now, but I can't seem to figure out how to change the applet to read the correct data.

Suggestions?

---

### Post by fabounet on 2009-12-11
Hi,
what gives ```
iwconfig
```
in a terminal ?

---

### Post by Docaltmed on 2009-12-11
iwconfig returns the following:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by fabounet on 2009-12-13
so eth2 is the interface for your wifi connection, isn't it ?

---

