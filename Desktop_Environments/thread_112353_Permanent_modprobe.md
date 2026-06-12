---
title: "Permanent modprobe"
date: 2006-01-04
forum: Desktop Environments
---

### Post by Vinze on 2006-01-04
Hey, I had problems connecting to the network, then from the Ubuntu Wiki I gathered that I had to do a modprobe with my drive, like this:

```
sudo modprobe -r acx_pci
```

It works, and I can now connect to the internet. My problem is, however, that I have to do this every time I start my computer. Does anyone know a way to do this permanently? 

Thanks in advance.

---

### Post by ahave2005 on 2006-01-04
Find the module acx_pci and move it to another location, ie /root.
Try this:
> find /lib/modules/`uname -r` -name "acx_pci"

If it succesfully finds the module:
> sudo find /lib/modules/`uname -r` -name "acx_pci" -exec mv {} /root \;

If this for some reason doesn't work, try to change directory to /lib/modules/2.6.xx-xx-386 where xx is your current kernel, and remove the module manually: sudo mv acx_pci /root

This should do the trick.
/ahave

---

### Post by SickTwist on 2006-01-04
[QUOTE=Vinze]Hey, I had problems connecting to the network, then from the Ubuntu Wiki I gathered that I had to do a modprobe with my drive, like this:

```
sudo modprobe -r acx_pci
```

It works, and I can now connect to the internet. My problem is, however, that I have to do this every time I start my computer. Does anyone know a way to do this permanently? 

Thanks in advance.[/QUOTE]

The command you are running is removing the acx_pci module from the kernel. If you want to block the module from being loaded in the first place, add the name of the module to /etc/hotplug/blacklist:

gksudo gedit /etc/hotplug/blacklist

Then just add "acx_pci" (without quotes) to the end of the file.

---

### Post by Vinze on 2006-01-04
[QUOTE=SickTwist]The command you are running is removing the acx_pci module from the kernel. If you want to block the module from being loaded in the first place, add the name of the module to /etc/hotplug/blacklist:

gksudo gedit /etc/hotplug/blacklist

Then just add "acx_pci" (without quotes) to the end of the file.[/QUOTE]

OK, thanks a lot, that'll be the one I'm looking for :D

---

