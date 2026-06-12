---
title: "Turning on Compiz on Ibix: Desktop effects could not be enabled"
date: 2008-12-06
forum: General Help
---

### Post by abcuser on 2008-12-06
Hi,
Ubuntu 8.10 I would like to turn on Compiz.

System | Preferences | Appearance | Visual Effects tab | I selected Normal option button and got error: "Desktop effects could not be enabled." Is there any way to check what is wrong, because this message doesn't tell anything about why effects can't be turned on?

Executing compiz command from Terminal I get output:
```

compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

Regards

---

### Post by DJ_Peng on 2008-12-06
What kind of video card do you have? You may need to get some updated video drivers.

Can you enable your video drivers in *System > Administration > Hardware Drivers*?

---

### Post by ubiworld on 2009-01-15
I have a laptop HP with GeForce Go 7600 and I cannot enable drivers. I went to System -> Preferences -> Appearance choose option Extra and tries to install but nothing.. error message 'Desktop effects could not be enabled'

Then I try System -> Administration -> Hardware Drivers. I choose 'NVIDIA accelerated graphics driver (version 177)', I click Activate, a windows with a progress bar starts, but disappear.. 

what can i do?

thx

---

### Post by Ahadiel on 2009-01-15
> **ubiworld said:**
> I have a laptop HP with GeForce Go 7600 and I cannot enable drivers. I went to System -> Preferences -> Appearance choose option Extra and tries to install but nothing.. error message 'Desktop effects could not be enabled'

Then I try System -> Administration -> Hardware Drivers. I choose 'NVIDIA accelerated graphics driver (version 177)', I click Activate, a windows with a progress bar starts, but disappear.. 

what can i do?

thx
Make sure your system is up to date then try again.
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

