---
title: "Nautilus path address, refractory issue"
date: 2012-01-14
forum: Desktop Environments
---

### Post by Sydesmo on 2012-01-14
Hi,

I have just install Ubuntu on my laptop (and wiped Windows, no going back now), but I am having problems changing the Nautilus address appearance from icon to path.

I looked at this help post [https://help.ubuntu.com/community/RestoreNautilusLocationBar](https://help.ubuntu.com/community/RestoreNautilusLocationBar) but when I go into d-conf tools to the location suggested there is no option available there to always use location entry. 

There is however, an option in g-conf tools to do this, but I have ticked this option and rebooted and it does not display the location as a path, still as icons.

I suspect this may be a problem I have brought on myself by using 11.10 with gnome classic but nevertheless I would be grateful if anyone knew how to remedy it.

I am running Ubuntu 11.10, on a Acer laptop and I restored the gnome classic view.

thanks

---

### Post by Krytarik on 2012-01-14
> **Sydesmo said:**
> I looked at this help post [https://help.ubuntu.com/community/RestoreNautilusLocationBar](https://help.ubuntu.com/community/RestoreNautilusLocationBar) but when I go into d-conf tools to the location suggested there is no option available there to always use location entry.
[..]
I am running Ubuntu 11.10 ...
Then just try the command line method:
```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```To disable that option again, just replace "true" with "false" in the command, obviously.

Btw., you don't need to reboot, that change takes effect immediately, you don't even need to re-open Nautilus.

Regards.

---

### Post by Sydesmo on 2012-01-14
This worked perfectly, thank you very much :)

---

