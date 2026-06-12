---
title: "4K fullscreen with fractional scaling not working with default drivers NVIDI1080ti"
date: 2022-01-24
forum: Desktop Environments
---

### Post by workmailtome on 2022-01-24
Fullscreen applications don't work with the default drivers installed at OS (ubuntu 20.04) install time (nvidia-driver-470). Attempting to use other drivers usually ends with me having to reinstall.

I have two 27" 4k monitors connected via display cables running at 60Hz. When i open a full screen application the application will open fullscreen on the primary monitor and than fill half of the secondary with a black box. This only happens with fractional scaling turned on. Are there any workarounds for this, or optional drivers i can install? anything above 125% scaling kinda defeats the purpose of having upgrading and switching the scaling back and forth can mess with running applications. Not all applications allow me to set the text or ui scale so the global display setting is pretty necessary

---

### Post by watchpocket on 2022-01-24
You may want to try to make sure you have the correct driver for your graphics card.  

I could be wrong, but if the card you have is an ***Nvidia GeForce GTX 1080 Ti***, the [Nvidia website where one can look up which driver goes with which card]("https://www.nvidia.com/en-us/geforce/drivers/") would appear to indicate that the latest updated driver for your card is driver 390.1470.

If so, it's better not to download it from the Nvidia site, but rather from either your Ubuntu repository, or from the "Graphics Drivers" PPA on Launchpad.net.  In which case you'd want driver 390.144 (this is the version on the PPA; the repository version would likely be an earlier one), which I assume would be the latest version optimized for Ubuntu.

You would do that by adding that PPA to your* /etc/apt/sources.list.d *by following the directions at that site:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal)

I was using the wrong driver for my card until a driver update suddenly wouldn't allow me to get past my login screen, and it took me a few weeks to figure out I was using the wrong driver.

Just make sure to not just necessarily believe me, and to satisfy yourself that you've got the appropriate driver for your GPU before you make any changes.

---

### Post by linuux on 2022-02-04
> **watchpocket said:**
> You may want to try to make sure you have the correct driver for your graphics card.  

I could be wrong, but if the card you have is an ***Nvidia GeForce GTX 1080 Ti***, the [Nvidia website where one can look up which driver goes with which card]("https://www.nvidia.com/en-us/geforce/drivers/") would appear to indicate that the latest updated driver for your card is driver 390.1470.

If so, it's better not to download it from the Nvidia site, but rather from either your Ubuntu repository, or from the "Graphics Drivers" PPA on Launchpad.net.  In which case you'd want driver 390.144 (this is the version on the PPA; the repository version would likely be an earlier one), which I assume would be the latest version optimized for Ubuntu.

You would do that by adding that PPA to your* /etc/apt/sources.list.d *by following the directions at that site:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal)

I was using the wrong driver for my card until a driver update suddenly wouldn't allow me to get past my login screen, and it took me a few weeks to figure out I was using the wrong driver.

Just make sure to not just necessarily believe me, and to satisfy yourself that you've got the appropriate driver for your GPU before you make any changes.
It appears (to me) that version 510 supports his card, too?

---

### Post by Autodave on 2022-02-04
510 is the newest driver.

---

### Post by linuux on 2022-02-04
> **Autodave said:**
> 510 is the newest driver.

Do you know if fractional scaling works  (in any of the flavors?)?  I noted that there are some 2020 posts and users claim it doesn't work (for them) - and then no one replied to them or they only had one or two replies.

It looked like it would work in Ubuntu - but, then people are talking about font and icon sizes - it looked like Ubuntu offered various choices of settings and then you can tweak the font and icon sizes too - some combination of settings should offer some choice?

---

### Post by him610 on 2022-02-04
Was not familiar with term, "fractional scaling" so I had to look it up. I did find this 'how to' on the internet, [https://www.maketecheasier.com/enable-fractional-scaling-gnome/]("https://www.maketecheasier.com/enable-fractional-scaling-gnome/")
Like every thing else, your mileage may vary.

---

### Post by linuux on 2022-02-05
> **him610 said:**
> Was not familiar with term, "fractional scaling" so I had to look it up. I did find this 'how to' on the internet, [https://www.maketecheasier.com/enable-fractional-scaling-gnome/](https://www.maketecheasier.com/enable-fractional-scaling-gnome/)
Like every thing else, your mileage may vary.
You must have a small monitor or still use 1080p res?   Or maybe even a 2K/1440p monitor?

For 4K and larger screens - the resolution means really tiny icons and text/fonts so you need to adjust the res or use fractional scaling.

If you research it more - you will find a lot of disgruntled Linux users complaining about how Linux developers/DE developers etc. utilize fractional scaling.   I can give examples if requested:  e.g. one was posted to askubuntu, I believe.  

I am currently using a failing HDD and planning on buying a SSD - so, I am not planning on installing Ubuntu onto it - waiting until I get a SSD.

But, in the meantime, I tried a number of Linux-based isos - and they all require me to use adjust the resolution because everything is just too small and I can't read the menu (KDE, XFCE for e.g.).  Ubuntu was easier because of the design of Gnome/GDM - but, fractional scaling still was preferred to increase the icon size. 

Thanks for the link but I knew about all that.  :)   But, what I said is true and I think it's strange how they all utilize different configuration settings and approach on how to deal with it (i.e. larger displays, larger resolutions - i.e. 4K and larger screens).  

Windows doesn't have this problem so a lot of Linux users are a bit critical (I think the criticism is constructive and warranted) that they haven't seriously addressed those issues.   Some users have jokingly said, that many of the developers will do so as they move to bigger 4K monitors. :)

---

### Post by him610 on 2022-02-05
> You must have a small monitor or still use 1080p res?
No, I have a 29 inch monitor; however, resolution could be 1080p - I don't know, but it is plenty good enough for me.

---

### Post by watchpocket on 2022-02-22
Beware of upgrading to nvidia-driver-510.  

A whole lot of folks -- including myself -- were not able to successfully perform the upgrade.  

My GPU is an Nvidia Gigabyte Geforce 3060, and I've decided -- after several upgrade attempts -- to stay with driver version 470.103.01.

As always YMMV but if you search around you'll see lots of nvidia-card users annoyed specifically about trying to upgrade to driver 510.  

And version 495 is apparently no longer available.

(I don't know anything more about the "why" of this.)

---

### Post by watchpocket on 2022-02-23
[I][B]UPDATE:
[/B][/I] 
Several folks on[ this Linux Mint forum]("https://forums.linuxmint.com/viewtopic.php?f=59&t=367590")  are having the same problem trying to update to nvidia-driver-510.   This may have something to do with the MATE desktop environment, as  those having the problem are all using the MATE DE, including myself,  though I'm on the Ubuntu-MATE OS, not the Mint OS.

I am guessing that the *Linux Mint *MATE DE is the same MATE DE used in the *Ubuntu-MATE OS* (though I could be wrong about this).

---

### Post by watchpocket on 2022-02-25
UPDATE: 
The root cause of this bug has been patched. See [this post on the Ubuntu-MATE forum]("https://ubuntu-mate.community/t/can-anyone-here-upgrade-to-nvidia-driver-510-without-login-problems/25147/4?u=watchpocket"), and indicate if it affects you.

---

