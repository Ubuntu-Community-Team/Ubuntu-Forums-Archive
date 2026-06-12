---
title: "netbook ubuntu and desktop ubuntu will not enable unity"
date: 2011-03-03
forum: Desktop Environments
---

### Post by gryer7421 on 2011-03-03
pretty simple.  i have a nvidia nvs160 in my laptop, and a nvidia 250/9800/8800 in my desktop.  i wanted to try out unity but it will not enable for either the desktop edition if ubuntu or the netbook (tried both on both devices)

after reading several other posts it seems that the nvidia driver does not support everything unity needs?  am i correct in understanding unity will not work until 11.04 ?

i am very new to linux in general, so i am trying to avoid 2 hours of command lines, especially since the wife would have no clue at all.

just looking for a "yay" or "nay" on stable nvidia support with the 175+ drivers.

---

### Post by gryer7421 on 2011-03-04
bump... no ideas ??

---

### Post by gryer7421 on 2011-03-09
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1)


so does this mean everyone with a nvidia driver will not be able to use unity

---

### Post by Krytarik on 2011-03-09
> **gryer7421 said:**
> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1)

so does this mean everyone with a nvidia driver will not be able to use unity
No, it doesn't, on the contrary! Driver support seems to be generally better for Nvidia cards/chips, at least by the proprietary driver.

The reason why the video driver for ATI/AMD cards/chips are mentioned more often or different, is that all the cards/chips produced before some 5 years aren't supported by the official proprietary driver anymore. Instead AMD made the source code of its driver available to the open source community, and the driver -also for those "legacy" cards- is developed parallelly by the "Open Source Edge" team.

So, you should get an appropriate driver by simply running the so-called "jockey", "System -> Administration -> Additional Drivers" (Gnome menu structure).

And you definetely need hardware-accelerated video to be able to run Unity.

---

### Post by gryer7421 on 2011-03-09
Tragically jockey did not help in either case.

driver 175 and 18x will not enable acceleration on the desktop, laptop or server.  (nvs160,geforce 880,9800,250) 

loaded both via jockey, enabled each one on 32/64 bit versions of netbuntu and Ubuntu desktop without success.

desktop effect will not launch and 3d accelerated apps do not render at all...

and worse so far nobody but you has responded...  (thanks btw)

---

### Post by gryer7421 on 2011-03-09
fyi, the cards in each system do list full ogl support... and are currently updated (at least on the windows side) and included in current driver releases..  i will have to look at nvidias driver faq for linux, it occurred to me maybe i should see if these cards are listed there for support.

---

### Post by gryer7421 on 2011-03-09
[http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html)

confirmed.  the 8800,9800,gts250 and the nvs 160m are supported in the 260 release series drivers.... but that made a light bulb go 
off!

jockey only offers 175 and 18x.... legacy drivers.  i think i need to retest by downloading the drivers myself and not trusting jockey ... 

thoughts ??

---

### Post by Krytarik on 2011-03-09
On each of your systems:
- remove *any* packages you find with "nvidia"
- add Ubuntu-X-Swat's PPA, they offer the most recent packaged version of the proprietary driver:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

```- install the "current" Nvidia driver and the settings package
```
sudo apt-get install nvidia-current nvidia-settings
```-run those command to create a proper "xorg.conf", just to be sure:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```- reboot/relogin

Btw., what versions of Ubuntu are you running on each machine?

---

### Post by gryer7421 on 2011-03-09
10.10 netbook and 10.10 unbuntu std,  i tried both 32 and 64bit editions.  im going to try the 32 bit desktop edition again with the new drivers from the 260 series. I'm willing to bet that or your instructions for updating aptget may help.  in hindsight i think im simply getting the wrong drivers from the base install.

oddly enough i do a full update before running jokey so i a m still surprised that the hardware is getting possibly mis-identified.

---

