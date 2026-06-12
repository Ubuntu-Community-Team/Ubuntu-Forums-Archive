---
title: "32 bit and 64 bit Nvidia Drivers | swrast driver missing"
date: 2015-09-13
forum: Gaming &amp; Leisure
---

### Post by Matty_Smith on 2015-09-13
I'm trying to get Steam working but I'm running into an error.

Here's the output from Steam
```

~ $ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-09-13 19:52:39] Startup - updater built Jun 16 2014 11:16:02
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

```

My graphics card is a GTX 970 and I'm using the proprietary nvidia driver version 355.06 (This isn't available through the default repositories so I downloaded a .run file from the nvidia website)
```

~ $ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)

```

I think I'm getting this error because Steam is looking for the 32 bit build of swrast (or some other graphics library) and I installed the 64 bit drivers. Do I also need to install the 32 bit drivers?

Can somebody help me? Thanks :-)

---

### Post by efflandt on 2015-09-13
It is generally recommended to use Ubuntu packages, so everything including updates are coordinated. I think there is something general planned to provide a source of more up to date graphics packages than from normal repositories. But for now I have been using nvidia-352 package for my GTX 750 Ti (which also has the new Maxwell chip) in 64-bit Ubuntu 14.04 from xorg-edgers ppa and have no issues with Steam or Steam games. I have not tried their nvidia-355 package yet.

But I am not sure how you would remove or purge drivers installed with a .run file because the usual package manager apt-get would not know anything about that.

swrast with or without kernel mode setting is in different paths for 32 and 64-bit:```
efflandt@XPS-8100-1404:~$ locate swrast
/usr/lib/i386-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/i386-linux-gnu/dri/swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
```

---

### Post by Matty_Smith on 2015-09-14
> **efflandt said:**
> It is generally recommended to use Ubuntu packages, so everything including updates are coordinated. I think there is something general planned to provide a source of more up to date graphics packages than from normal repositories. But for now I have been using nvidia-352 package for my GTX 750 Ti (which also has the new Maxwell chip) in 64-bit Ubuntu 14.04 from xorg-edgers ppa and have no issues with Steam or Steam games. I have not tried their nvidia-355 package yet.

But I am not sure how you would remove or purge drivers installed with a .run file because the usual package manager apt-get would not know anything about that.

swrast with or without kernel mode setting is in different paths for 32 and 64-bit:```
efflandt@XPS-8100-1404:~$ locate swrast
/usr/lib/i386-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/i386-linux-gnu/dri/swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/kms_swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
```

Wow, thanks :)
Steam and its games are working perfectly now.

I uninstalled the old drivers with
```

~ $ sudo ./NVIDIA-Linux-x86_64-355.06.run --uninstall

```

Then I added the xorg-edgers PPA
```

~ $ sudo apt-add-repository ppa:xorg-edgers
...
~ $ sudo apt-get update

```

Installed the new drivers and then rebooted
```

~ $ sudo apt-get install nvidia-355
...
~ $ reboot

```

**edit:** according to the xorg-edgers page, I need to link to it
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

---

