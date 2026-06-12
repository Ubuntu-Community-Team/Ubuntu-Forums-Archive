---
title: "System Update error"
date: 2005-08-20
forum: Desktop Environments
---

### Post by chrisod on 2005-08-20
I'm getting the following error when trying to apply the kernal upgrade that was released a couple of days ago.
> 
E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.4_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko', which is also in package ipw220

I tried renaming the ieee80211 directory  - it doesn't help. Update gives me the same error. 

Is there a way to force the system update tool to force-overwrite?

Is it worth worrying about? With Breezy coming in the next couple of months anyway...

---

### Post by woedend on 2005-08-20
[QUOTE=chrisod]I'm getting the following error when trying to apply the kernal upgrade that was released a couple of days ago.


I tried renaming the ieee80211 directory  - it doesn't help. Update gives me the same error. 

Is there a way to force the system update tool to force-overwrite?

Is it worth worrying about? With Breezy coming in the next couple of months anyway...[/QUOTE]
 i believe in command line the -f option with apt forces it...with synaptic when i get that error i first check for broken packages...if there are none i just keep trying to install and it usually works the 2nd or 3d time.

---

