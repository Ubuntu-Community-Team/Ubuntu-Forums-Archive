---
title: "Beryl in ubuntu"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by quarkhirad on 2007-10-21
Hi guys. I just installed ubuntu 7.10 gutsy . It is a really nice distro. However when i had 7.04 on my system i installed beryl using apt -get sudo apt-get install beryl beryl-manager emerald-themes . I would like to install beryl again but it seems to have been removed from the ubuntu repositories. This is because when i type sudo apt-get install beryl beryl-manager emerald-themes in apt -get i get the message that the package beryl is not found. Can someone please tell me how to install beryl in ubuntu 7.10:confused::confused::confused: :(

---

### Post by corney91 on 2007-10-21
> **quarkhirad said:**
> Hi guys. I just installed ubuntu 7.10 gutsy . It is a really nice distro. However when i had 7.04 on my system i installed beryl using apt -get sudo apt-get install beryl beryl-manager emerald-themes . I would like to install beryl again but it seems to have been removed from the ubuntu repositories. This is because when i type sudo apt-get install beryl beryl-manager emerald-themes in apt -get i get the message that the package beryl is not found. Can someone please tell me how to install beryl in ubuntu 7.10:confused::confused::confused: :(

Beryl and Compiz have merged to make Compiz Fusion, which is installed by default in gutsy. If you install the compiz settings manager you can change the settings much like you would have been able to in Beryl.

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by quarkhirad on 2007-10-21
Thanks corney91 :guitar::guitar::guitar::):):):KS:KS

---

### Post by axle_foley00 on 2007-10-21
Compiz and Beryl as far as I'm aware have merged again into Compiz Fusion. Also since Compiz should be enabled by default in Gutsy Gibbon, if you go to the appearance tab you can actually set "Desktop Effects" to a higher value to get some of the effects you are used to. If however you want more control over the Compiz effects then do the following:

Go to Synaptic and search for *compizconfig-settings-manager*

Let me know if that helps.

---

### Post by axle_foley00 on 2007-10-21
Sigh...I guess conery91 beat me to it.

---

### Post by corney91 on 2007-10-21
> **quarkhirad said:**
> Thanks corney91
My pleasure:)
You'll find Compiz has many more options than Beryl, so it'll probably take longer to configure. But, of course, will look better:).

---

