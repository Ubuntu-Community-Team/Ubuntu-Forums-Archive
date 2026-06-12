---
title: "Virtualbox usb devices not visible"
date: 2009-06-07
forum: General Help
---

### Post by SatieB on 2009-06-07
Hi,

I'm using VirtualBox 2.1.4_OSE and it's working fine except for the usb devices.
Took a look at [http://ubuntuforums.org/showthread.php?p=7345104](http://ubuntuforums.org/showthread.php?p=7345104) and followed the advise:

[LIST]
[*]installed guestAdditions
[*]added divged 119 to /etc/fstab
[*]added myself to vboxusers
[/LIST]
The usb devices remain stil greyed out ("no available devices").

Any hints?

---

### Post by keplerspeed on 2009-06-07
The OSE edition does not have usb support. You will have to download and install the PUEL (non-free) version off the virtualbox website: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

A good guide for the above installation of the PUEL version is here [http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html)

Then follow this to enable usb: (Thanks rfs1970!!! [http://ubuntuforums.org/showthread.php?t=1155643](http://ubuntuforums.org/showthread.php?t=1155643))

Enter this into a terminal:
```
sudo gedit /etc/fstab

```
At the end of the file add this line:
```

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```
Now save the file, then:
```

sudo mount -a

```

Finally, go to system>administration>users and groups and click 'manage groups'. Find vboxusers and ensure you are added to this group (your box ticked). Let me know how it goes!

---

### Post by SatieB on 2009-06-07
> **keplerspeed said:**
> The OSE edition does not have usb support. You will have to download and install the PUEL (non-free) version off the virtualbox website: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)



Thanks!
I presume that I have to deinstall the ose version first?

---

### Post by keplerspeed on 2009-06-07
Oh yes.. sorry. So open up synaptic from system>admin>synaptic and seach for virtualbox. The OSe version should appear, right click on it and remove. Now click the apply tick up the top of the synaptic window. Virtualbox-OSE will be uninstalled.

Oh thats right kubuntu.. well im sure synaptic is around somewhere....

---

### Post by SatieB on 2009-06-11
It took me some days to start, but I finished the installation this evening. Worked like a charm! 
I followed the advise: VitualBox is up and running, but usb devices are still not working although they are not greyed out anymore.
I've added a filter for a memory stick, rebooted, but no joy.
What did I do wrong?

---

