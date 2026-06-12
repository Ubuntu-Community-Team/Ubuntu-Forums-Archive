---
title: "Unable to access Synaptics"
date: 2009-02-26
forum: General Help
---

### Post by drifter2502 on 2009-02-26
Urgent! I cannot get into Synaptics Manager. I am getting the following message and I just do not know what to do next...
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
If I paste above in terminal I get this..~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Just prior to this I was had a failed download of an essential security update- flshget-free (I think it is called) Anyway I cannot get net radio.you tube etc. All ok before.

---

### Post by taurus on 2009-02-26
Add the sudo in front of the command for root privilege.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by drifter2502 on 2009-02-26
Thanks taurus, will go off and try. Drifter.

---

### Post by drifter2502 on 2009-02-26
> **drifter2502 said:**
> Thanks taurus, will go off and try. Drifter.

taurus, that worked so well. Thank you so much. Off for a lie down to reduce blood pressure.

---

### Post by taurus on 2009-02-26
> **drifter2502 said:**
> taurus, that worked so well. Thank you so much. _Off for a lie down to reduce blood pressure_.

Maybe you need to go outside for some fresh air!

---

