---
title: "Beryl update failed - no plugins will load"
date: 2007-02-01
forum: Desktop Environments
---

### Post by Foxblood on 2007-02-01
Update manager alerted me to upgrades, mostly having to do with Beryl. All of the updates went ok except the Beryl plugins update. Now my Beryl is messed up. The Beryl manager has very few options, Beryl-core only. If I can't get the new package to install, how do I go about using the older version? The error message I get is this:

E: /var/cache/apt/archives/beryl-plugins_0.1.9999.1~0beryl1_i386.deb: trying to overwrite `/usr/lib/beryl/libimgjpeg.so', which is also in package beryl-plugins-extra

Any help anyone can offer would be greatly appreciated.

---

### Post by tchoklat on 2007-02-01
not sure - but a good bet may be to un-install beryl through Automatix and then install it again. You can then do a sudo aptitude update and then an sudo aptitude upgrade


tony

---

### Post by glabouni on 2007-02-01
[http://ubuntuforums.org/showthread.php?t=351319](http://ubuntuforums.org/showthread.php?t=351319)

---

### Post by Foxblood on 2007-02-01
Same thing, same error message.

---

### Post by jornahow on 2007-02-01
I had the same problem.  I tried to resolve it through synaptic by forcing synaptic to downgrade the packages.  This didn't work - it left me with a broken packages message.  I solved the problem by using synaptic to completely remove all beryl packages and then i reinstalled the latest packages, again using synaptic.  Now all is working fine and I have some features that didn't work in the last update, eg window thumbnails.  There are also some new animations.

jornahow

---

### Post by Michelpt on 2007-02-01
The same problem I also had with falling of the plugin update with the 1.9999 version. More, when I uninstalled beryl, beryl-manager, etc. I restarted the Xserver and could not get the GUI at all. When I looked through xorg.conf I saw 1:5:0 nvidia settings on my PCI bus, when I had 1:0:0, one else funny thing: the parameter "load "GLcore" in the Module section was missed, I had also "driver "nv" instead "driver "nvidia" in the Device section and the screen resolution was also changed. Gracias to xorg.conf_back_up file my graphics was recovered and after the next time installing of the newest Beryl through Adept Package Manager I can it run.  Any advise how it happened and why the graphics was misconfigured? (Running at Kubuntu Edgy Eft amd_64, graphics Nvidia GForce 7300 Go 256 Mb)

---

### Post by Foxblood on 2007-02-06
> **jornahow said:**
> I had the same problem.  I tried to resolve it through synaptic by forcing synaptic to downgrade the packages.  This didn't work - it left me with a broken packages message.  I solved the problem by using synaptic to completely remove all beryl packages and then i reinstalled the latest packages, again using synaptic.  Now all is working fine and I have some features that didn't work in the last update, eg window thumbnails.  There are also some new animations.

jornahow

Thanks, jornahow, all is well in Beryl land again. Plus I also got the new stuff, too.

---

