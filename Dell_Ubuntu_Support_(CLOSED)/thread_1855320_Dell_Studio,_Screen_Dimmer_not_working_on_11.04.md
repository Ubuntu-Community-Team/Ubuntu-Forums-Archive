---
title: "Dell Studio, Screen Dimmer not working on 11.04"
date: 2011-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bond17_007 on 2011-10-05
Hi, I just installed 11.04 64bit, on Dell Studio 1558. (i3, Intel Graphics HD).
The screen is really bright when I click on the dimmer button from the keyboard, I do see the brightness applet show the dimmer bar go down however, the actual screen brightness does not change. I checked for updated driver etc . No Luck.
Can someone please help me get this thing resolved.
Thanks,

---

### Post by reacharavindh on 2011-10-26
I also face the same problem  .. The dimmer graphics seem to appear properly but does not decrease/increase brightness as expected ... could any body help ? ?

---

### Post by bond17_007 on 2011-10-29
I finally was able to resolve this issue using Kernel parameter.
Here is how I fixed it:

edit the grub file
```

$ sudo gedit /etc/default/grub  

```
Update GRUB_CMDLINE_LINUX_DEFAULT to include "acpi_backlight=vendor"

Below is the line from my file

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

```

After this is completed, you update grub

```

$ sudo update-grub

```

Reboot the system. And you have have the dimmer working..

Hope this helps!

----------------
There is a open ticket in launchpad if any of you are interested to follow:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611)

More about boot parameters here: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

