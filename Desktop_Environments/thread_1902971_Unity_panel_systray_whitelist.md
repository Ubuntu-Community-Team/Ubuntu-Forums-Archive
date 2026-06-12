---
title: "Unity panel systray whitelist"
date: 2012-01-01
forum: Desktop Environments
---

### Post by dualityim on 2012-01-01
I'm trying to get the Unity panel in Ubuntu 11.10 to show the applets of some of my programs but am not sure how to configure Unity to do so. The specific programs are VMware Workstation, Cisco AnyConnect VPN Client, and SparkleShare. I'm able to get their systray applets to show up by changing the systray-whitelist setting in gsettings to 'all', but doing that makes the Empathy applet show up too, which is made redundant by the default messaging applet. So it looks like I need to individually whitelist the programs I use, but how do I find out what names to use to whitelist them? I tried using the names of the binaries but it doesn't seem to work. Alternatively, is there a way to just blacklist the Empathy applet, rather than whitelisting everything else?

---

