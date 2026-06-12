---
title: "Cannot access secure sites!!"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Hitman1 on 2005-10-29
For some odd reason, my kubuntu 5.10 install stopped being able to access any secure web site like banks and so.

I tried firefox, konqueror, and even IE on wine. All three can load any web site just fine except if the site is a secure site that has an https instead of http. The laptop which is having this problem is a dual boot with XP. In XP, I can access all secure sites with no problem so it is kubuntu specific! Note that this problem developed just lately; the same install was able to access secure sites perfectly. Something happened that made it stop and I can't figure out what caused it. 

What could be the problem here?

---

### Post by towsonu2003 on 2005-10-29
Did you by any chance installed a firewall or played around with ip tables? this looks like a port/firewall issue. If u installed a firewall (like firestarter), make sure port 443 (which is https) is allowed. 

Also, try to make a map of what you did in kubuntu before this started.
other than that, i have no idea, sorry :(

good news: i'm a newbie :)

---

### Post by super on 2005-10-29
check your firefox settings
tools-->options-->advanced-->security or certificates

this section has the settings for browsing secure sites

---

### Post by Hitman1 on 2005-10-30
I did a sudo iptables -L, and there is no rules at all; just the default ACCEPTs.

I checked the firefox preferences and everything is set alright. I've tried konqueror and IE (on Wine) and they both have the same problem so it is not firefox specific. Is there any package that kubuntu needs to be able to access secure sites? I remember from redhat, to access any secure site you must install mozilla-psm. Do I need something like that in ubuntu?

---

### Post by nivok on 2005-11-06
I know if your date is off it won't accept any certificates, worth checking to make sure the date is set right

---

