---
title: "dead x server!"
date: 2007-04-24
forum: Desktop Environments
---

### Post by jiggling_john on 2007-04-24
I just tried installing the nvidia drivery with Envy and it has murdered my installation of ubuntu (7.04).

I can no longer start the x server. I've tried running envy from command prompt, doing a remove and reintsall but still no joy. The error i get is "failed to start the x server - it is likely that it is not set up correctly"

How can I fix this without reinstalling ubuntu and losing my setup?!

---

### Post by taurus on 2007-04-24
Just reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Use **vesa** driver for now until you get X running again.

---

### Post by Aetherius on 2007-04-24
EDIT: I was typing this when I was beat to it ;)


get to the command line and type

```
sudo nano /etc/X11/xorg.conf
```

move down to the 'Device' section and locate the line where it should say

```
Section "Device"
        Identifier      "Nvidia......whatever"
        Driver          "nvidia"
        BusID           "PCI:0:2:0"
EndSection

```

or something similar, change the Driver from "nvidia" to "nv" so it reads similar to

```
Section "Device"
        Identifier      "Nvidia......whatever"
        Driver          "nv"
        BusID           "PCI:0:2:0"
EndSection

```

and you should be able to start X just fine. No fancy effects or hardware acceleration tho.

---

### Post by Aetherius on 2007-04-24
selecting 'nv' would be more appropriate than 'vesa' would it not?

---

### Post by jiggling_john on 2007-04-24
neither of the above work....

i get one of 2 erros. the first being "etc/init.d/kdm command not found"

or

unable to find a valid frame buffer device
screens found, but none have a usable configuration

what now?!

---

### Post by jiggling_john on 2007-04-24
I ran envy from the command prompt, did a manual install of the new legacy nvidia driver... this seemed to work, gnome booted up... so i tried a restart of the system and... broken X again... what's going on?!

---

### Post by plowshares on 2007-04-24
I could have sworn that there was another part of this thread about restoring the backup from envy with sudo cp in here earlier...

---

### Post by taurus on 2007-04-24
```
sudo cp /etc/X11/xorg.conf.backup  /etc/X11/xorg.conf
```

---

