---
title: "How to close stalonetray?"
date: 2012-10-18
forum: Desktop Environments
---

### Post by PeterTaps on 2012-10-18
Folks,

I am running Minimal Ubuntu + Openbox. To bring up the network manager UI, I created the following script as suggested at [https://wiki.archlinux.org/index.php/NetworkManager#Openbox](https://wiki.archlinux.org/index.php/NetworkManager#Openbox).

 #!/bin/sh
 nm-applet    > /dev/null 2>/dev/null &
 stalonetray  > /dev/null 2>/dev/null
 killall nm-applet

The idea is to release nm-applet memory after done with it.

When I run this script, stalonetray comes up as expected. However, there is no option to close the tray. 

Is there something that I am missing?

Thank you in advance for your help.

Regards,
Peter

---

