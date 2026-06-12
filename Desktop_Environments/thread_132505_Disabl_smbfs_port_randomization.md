---
title: "Disabl smbfs port randomization?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by cheuschober on 2006-02-18
Hiya -- curious to know if anyone knows how to disable port randomization with mounting a samba share?

I have an M$ x64 box with a few shares I'm trying to mount on my . The x64 box has an application firewall on it configured to the level that all M$ firewalls must, especially in highly populated urban areas -- to the point of utter paranoia.

I was trying to set a rule to allow the necessary TCP traffic through but each time I issue the mount command smbfs tries to connect on a different set of ports (both remote and local) that appear seemingly at random. I'd prefer not to just allow any and all tcp traffic between my x64 ip and my client ip. Is there a way to force samba to use static ports?

Many thanks,
~C

Edit: D'oh... 'e' key is on the fritz sorry about the title! :-p

---

