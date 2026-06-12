---
title: "Intel PRO 3945 Wireless on 2.6.24 (Debian Lenny 64-bit)"
date: 2008-05-21
forum: Debian
---

### Post by dfreer on 2008-05-21
Hi everyone,

  So I recently upgraded to lenny, and I noticed my wireless was no longer working. Noticed that in the description for firmware-ipw3945 that it is now depreciated, and it seems that I should now be using iwlwifi + mac80211. I was just wondering what is the correct procedure for getting my wireless back up and running?

---

### Post by p_quarles on 2008-05-21
The package you need is called firmware-iwlwifi, and is in non-free. The other component (iwl3945) is in the kernel already.

---

### Post by dfreer on 2008-05-21
I noticed the firmware-iwlwifi, and installed it. Only nothing shows up in iwconfig? Is there something else I'm missing?

---

### Post by p_quarles on 2008-05-21
> **dfreer said:**
> I noticed the firmware-iwlwifi, and installed it. Only nothing shows up in iwconfig? Is there something else I'm missing?
Well, in my experience, the kernel module loads up automatically, but if it didn't for you, you can try this:
```
# modprobe iwl3945
```
Then, see if it starts working.

---

### Post by Raven_Oscar on 2008-05-22
I am agree with p_quarles that kernel module should be loaded automatically.
In my own experience after upgrade from Etch to Lenny the only thing I did was installing firmware-iwlwifi. But it concerns 32 bit  version.

---

### Post by dfreer on 2008-05-22
Thanks guys! I now have wlan0-rename in my iwconfig/ifconfig list! Evidently, it took a full reboot and not having the ipw3945 being completely uninstalled, firmware-iwlwifi installed, and then a full reboot (modprobe successfully inserted, but I still didn't have a wlan until after a full reboot). 

Now to test whether I can successfully connect to my router.

---

### Post by yetkin on 2008-09-13
Can you explain this in details?  
i'm still having problems with lenny amd64 unstable

"Couldn't find package ipw3945-modules-2.6.25-2-amd64"
[URL="http://wiki.debian.org/ipw3945#head-c8e358933aa24d79cf78c9fbb03b5be057c85080"]
"Note: Since 2.6.24, There's a new module iwl3945 that supersedes ipw3945 ! The module was merged from the iwlwifi project and no longer requires a binary daemon. ipw3945 usage is not supported for Debian Lenny and Unstable users."[/URL]

---

