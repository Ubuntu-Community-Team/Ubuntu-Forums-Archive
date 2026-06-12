---
title: "must activate ath0 each use"
date: 2006-03-16
forum: Desktop Environments
---

### Post by ramdez on 2006-03-16
Hello all, I started with Ubuntu 5.10 and then switched to Kubuntu. (same machine).  I had my wireless dlink pci card working fine.  The card activated on boot and stayed connected.  Now that I'm running kubuntu, at first, the ath0 card was not even seen as activated (even tho a prog in ubuntu showed that itw as).  I'd click to activate and it would just flash activated and then go back to deactivated (even tho it was still on). 

Now, I find that it's working fine, i'm using WEP successfully.  However if I leave the computer sit for a few hours when I come back the only way to get back online is to deactivate and reactive the device.  I'm forced to do this through the windows wireless drivers tool.  I don't lose my IP for ath0 but it seems like I just need to wake it up or refresh it after each pause of a few hours. Does anyone know whats going on here? Thanks.

---

### Post by super on 2006-03-16
i dont know how to solve your problem but maybe instead of doing the whole ndiswrapper thing you could do this:
```
sudo /etc/init.d/networking restart
```

i think it should retart the network with out losing your windows wireless tools settings

---

