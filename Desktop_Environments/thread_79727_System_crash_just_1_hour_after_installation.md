---
title: "System crash just 1 hour after installation"
date: 2005-10-20
forum: Desktop Environments
---

### Post by kai.springer on 2005-10-20
Hello there,

I just wanted to post my unlucky experiences concerning the new Breezy Badger release. After the installation, which worked really fine, I tried to convince my D-Link AirPlus DWL-650+ Adapter to connect to the network. Breezy even doesn't recognize there is a wireless card in the pc card slot. I mean, I can understand when it says card isn't known and asks for a workaround or a device driver. But there is no response. Then, hoping to find an easy solution on the internet, I attached my lan cable. On Hoary that worked but when I opened the network settings tab in system settings, I had another astonishing surprise. The "admin" button is not to be seen on the screen as the window is larger than the screen itself and can't be shrinked. Pressing Alt+F2 und typing kdesu kcontrol helped. The network card configured itself correctly via DHCP and I thought this would be fine then. But it wasn't; Konqueror kept telling me that there is no connection to the internet though I could connect to the access page of the router on 192.168.... I restarted the computer then, and surprise, the complete system crashed telling me I should type my login name and password but not starting KDE. So far I haven't changed any system setting except the settings for DHCP on eth0.

I must admit I haven't made my mind up about another try for Breezy Badger with a new installation, but at the moment I won't. I really don't get rid of the feeling of a bad beta release. :confused:

---

### Post by daller on 2005-12-01
Have you tried to configure the X-server again? 

```
sudo dpkg-reconfigure xserver-xorg 
```

...I solved my X-issue that way! 

What is the output from a "startx"?

---

