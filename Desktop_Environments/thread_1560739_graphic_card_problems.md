---
title: "graphic card problems"
date: 2010-08-25
forum: Desktop Environments
---

### Post by vaina on 2010-08-25
Hi everybody,

   I recently installed Ubuntu 10.04 on a little workstation (DELL Precision 490), with an NVIDIA Quad FX 550 graphic card. Then i downloaded and installed the recommended proprietary drivers by *System/Administration/Driver hardware* (I guess I need vers. 173). Visualization and resolution seemed good, but I had some problems in computer restarting (it freezes) and with a specific work software, so I manually installed the most recent drivers from the productor's site, after the following [procedure]("http://ubuntuforums.org/showthread.php?t=1467074") (*post #1*). The new drivers installation seemed OK, but previous problems still remained (I also noticed that standby modality, when the computer is inactive, freezed it and I had to reboot).
After that I went on to read the above thread and I followed the suggestion in *post #74*, linking to repository [ppa:ubuntu-x-swat/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates"). Then I also installed the package **nvidia-graphics-drivers-173** by the packages manager and I removed the lines added in **blacklist.conf** with the previous manual installation

```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```I rebooted the computer. Installation seems OK again, but I checked the installed drivers by *System/Administration/Driver hardware* and i read the message [COLOR=blue]*This driver is activated, but not in use*[/COLOR]. How can I fix the problem? What i mistook on my steps? Thanks for your help.

---

### Post by vaina on 2010-08-27
is there anybody out there?

---

