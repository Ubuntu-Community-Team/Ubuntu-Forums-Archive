---
title: "Reinstall sound drivers?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by lawngn0mex on 2006-06-09
Hello,

I was attempting to install the realtek drivers from their site on my Dapper install. 

This has worked on Breezy, as well as the early Dapper betas. The reason I used these drivers over what came with the distro is because it was essentially an automatic way to get Spdif working, without having to manually hack up asound.conf, or any convoluted process really. Sound did work before this. Just never digital audio (spdif) hell, the drivers (from realtek) would send all audio out of spdif.


The problem lies in the fact that alsaconf isn't part of the alsa packages now, and the drivers rely on it to set everything up. The bad part is the drivers also remove all of the old sound drivers as part of the install script:
```

echo "Remove old sound driver"
if [ -d /lib/modules/$KERNEL_VER/kernel/sound ]; then
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/pci
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/acore
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/driver
fi

```

Since the install won't work without alsaconf, I was wondering if anyone knew which packages from the repository I'd have to reinstall, as well as if a dpkg-reconfigure would work, or if I'd have to actually remove the packages, and replace them. 


This is where you can grab the linux driver and check them out if you so desired.
[http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True)

Since there's obviously no sound drivers... here's what alsamixer tells me. ](*,) 
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

---

