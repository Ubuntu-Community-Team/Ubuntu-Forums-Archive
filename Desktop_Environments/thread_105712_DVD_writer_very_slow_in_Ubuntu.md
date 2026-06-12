---
title: "DVD writer very slow in Ubuntu"
date: 2005-12-19
forum: Desktop Environments
---

### Post by diffuser78 on 2005-12-19
I migrated to Ubuntu 6 months back and have been fan of everything except that it burns my DVDs very slow. I have a 16X dual layer burner. I use K3b to burn DVDs. While Nero on my Windows partition runs much faster, I have no clue why Ubuntu doesn't detect the correct speed of my writer.

Any help is appreciated,

Thanks

---

### Post by schilcha on 2005-12-19
Is DMA-mode enabled for your dvd-burner?

On the console, try ```
hdparm -d /dev/hdc
```
(substitute hdc with whatever your dvd-device is)
If you get something like
> /dev/hdc:
 using_dma    =  1 (on)
just skip the rest of my suggestions...

If dma is "off", try to enable it using ```
sudo hdparm -d1 /dev/hdc
```(again with your dvd-device instead of hdc). If this fails or you want to know how to make this change permanent, check [this thread]("http://www.ubuntuforums.org/showthread.php?t=19519") or [http://ubuntuguide.org/#speedupcddvdrom]("http://ubuntuguide.org/#speedupcddvdrom") for instructions.

---

### Post by rizzyc on 2006-01-03
i dont know what my dvd drive is? My dvd burner wont burn above 1.0 in k3b and gnome baker

---

