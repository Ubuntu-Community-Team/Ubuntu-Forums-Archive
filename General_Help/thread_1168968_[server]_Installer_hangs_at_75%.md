---
title: "[server] Installer hangs at 75%"
date: 2009-05-24
forum: General Help
---

### Post by fiddler616 on 2009-05-24
Hello,
I'm installing USE Hardy on an old desktop (64MB RAM, 433? mHz processor, 4.4GB HDD) and the installer was going quite well. Now, though, it's hung at "75% Storing language" (it's lasted over an hour with no gain). I pressed <Alt><F4> and it says:
```

<trim>
<timestamp> localechooser:    en_US.UTF-8...
```
(spaces intentional).

What's going on? Is there any way I can fix it?


Thanks.

---

### Post by SabreWolfy on 2009-06-15
I can confirm this on a PIII 450MHz with 64MB RAM and a 6.5GB HDD with Jaunty Server. Installation went smoothly until 74%, saying "storing languages". Alt-F4 simply showed the DHCP renewal messages (as I'd left if for about 90 minutes). The HDD was thrashing all the while, so I assumed it was doing something. I've rebooted and started the installation again, but I'm not hopeful. It's a pity, because I thought 64MB for a console-only Server installation would be fine.

[This]("https://help.ubuntu.com/community/Installation/LowMemorySystems") link appears to suggest that a "command-line" installation from the Alternate CD is preferable to a Server installation for low-memory systems. I may try that if the second Server install also hangs at 74%.

Both the Server and Alternate CD's hang at 74%. I switched to a terminal and KILLed the localechooser process and the installation continued, but I later aborted it anyway.

I successfully installed from both the Server and Alternate CDs after adding another 64MB of RAM to the machine. The installations went much faster than with 64MB of RAM and the "storing languages" section only took a few seconds to complete. However, both installations failed on the first boot with a segmentation fault and/or call trace error.

I then tried Xubuntu 8.04.1 Alternate CD command-line only installation. This worked perfectly and booted. However, the wired ethernet was not working, so I aborted the whole project.

---

