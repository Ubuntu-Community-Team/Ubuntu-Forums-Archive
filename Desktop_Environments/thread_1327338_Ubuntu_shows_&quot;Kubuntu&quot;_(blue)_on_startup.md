---
title: "Ubuntu shows &quot;Kubuntu&quot; (blue) on startup &amp; shutdown after Kubuntu Desktop install"
date: 2009-11-15
forum: Desktop Environments
---

### Post by youbuntu on 2009-11-15
Hi there - I have just installed the kubuntu-desktop package, and now, every time I boot or shutdown, I get the VERY VERY UGLY, blue "Kubuntu" logo, along with it's ghastly progress bar.

Please would someone tell me how I reset this to the default *Ubuntu* one?.

Thanks.

---

### Post by Zorael on 2009-11-15
> **glossywhite said:**
> the VERY VERY UGLY, blue "Kubuntu" logo
:<

```
$ sudo update-alternatives --config usplash-artwork.so
*<pick usplash-theme-ubuntu.so>*
$ sudo update-initramfs -u -k all
```

---

### Post by youbuntu on 2009-11-15
> **Zorael said:**
> :<

```
$ sudo update-alternatives --config usplash-artwork.so
*<pick usplash-theme-ubuntu.so>*
$ sudo update-initramfs -u -k all
```

Thanks so much for your help.

---

