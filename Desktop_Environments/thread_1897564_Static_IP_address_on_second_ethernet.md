---
title: "Static IP address on second ethernet"
date: 2011-12-19
forum: Desktop Environments
---

### Post by Jonathan L on 2011-12-19
Hi All

I've got a system which is running Live CD image of 10.04.3 Desktop.  It has a second ethernet interface which I've given a static address with 
```
ifconfig eth1 192.168.2.66
```It works fine.  However, after a while -- perhaps 30 minutes -- something stops it  (but it can easily be restarted with ifconfig down then ifconfig up).  Is there something in the desktop environment which might do this?  Any ideas how to disable that?

Any tips most welcome.

Kind regards,
Jonathan.

---

### Post by thaelim on 2011-12-19
It's probably network manager doing that. You would be better off using network manager to configure the static IP, that way you won't have it overwriting your manual config. nn-connection-editor is the one you want.

---

### Post by Jonathan L on 2011-12-20
> **thaelim said:**
> It's probably network manager doing that. You would be better off using network manager to configure the static IP, that way you won't have it overwriting your manual config. nn-connection-editor is the one you want.

Thanks Thaelim, that's exactly what is needed.

My system is actually running unattended, so I need to script it.  I found
```
sudo apt-get purge network-manager network-manager-gnome
```

Which seems like it does the right thing.

Thanks again.
Jonathan.

---

