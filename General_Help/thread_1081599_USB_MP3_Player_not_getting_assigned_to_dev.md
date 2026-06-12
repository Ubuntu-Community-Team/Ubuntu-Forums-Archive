---
title: "USB MP3 Player not getting assigned to /dev"
date: 2009-02-26
forum: General Help
---

### Post by lotsofish on 2009-02-26
I've searched these forums and the web, but I haven't found anything that works yet.

I have a Memorex MMP8585 MP3 player I'm trying to get to work with Ubuntu. When I connect it to the computer through USB, nothing happens. It doesn't automount and it doesn't even show up as a device in /dev. Normally, if something doesn't automount, it still shows up as a device that I can manually mount, usually as /dev/sdb1. When I hook up another MP3 player, my phone or a USB thumbdrive, they all automount without any problems.

I tried it on two different Ubuntu (8.10 and 8.04) computers and also on a different one running PCLinuxOS (TinyME 2008) all with the same results.

Can anyone help?


dmesg
```

[109348.681024] usb 2-5: new high speed USB device using ehci_hcd and address 8
[109348.816174] usb 2-5: configuration #1 chosen from 1 choice

```


lsusb
```

Bus 002 Device 008: ID 10d6:2300 Actions Semiconductor Co., Ltd

```

---

### Post by lotsofish on 2009-02-26
Bump?

---

