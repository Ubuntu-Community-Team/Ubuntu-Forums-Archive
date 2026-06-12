---
title: "Connecting BQ Aquaris E 4.5 Ubuntu Edition phone to laptop running Fedora"
date: 2015-05-01
forum: Fedora/RedHat and derivatives
---

### Post by kjell159 on 2015-05-01
Hello, I got me an Ubuntu Phone lately but my pc cannot find the phone when I connect it through USB?
I had absolutely no problems connecting my other smarthpone -which is literally dead for quite a while now- which ran an Android 4 version (it was also a pretty old smartphone) and other peripheral USB devices like these with my Linux pc.
I'm running Fedora 20 on a Linux 3 kernel.

```
$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:d20c Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by kjell159 on 2015-05-03
Now it's working!
I guess installing the richt mtp package, updating and rebooting worked as it now gets recognised and I can go through the folders everytime I plug it in.

---

