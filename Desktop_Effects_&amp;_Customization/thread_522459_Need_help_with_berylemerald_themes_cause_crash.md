---
title: "Need help with beryl/emerald themes cause crash"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by gecko94 on 2007-08-10
Try and try as I might I can't get emerald to work for me at all. If I do an install of ubuntu and install beryl, it will work great with metacity as the theme manager. If I attempt to even install emerald, beryl will no longer use metacity and it will not work anymore. If I use synaptic to uninstall every package and do a reinstall of beryl without emerald I will be unable to get it to work again unless I reinstall ubuntu. I would really appreciate some help. 

thank you,

gecko94:KS

---

### Post by overdrank on 2007-08-10
> **gecko94 said:**
> Try and try as I might I can't get emerald to work for me at all. If I do an install of ubuntu and install beryl, it will work great with metacity as the theme manager. If I attempt to even install emerald, beryl will no longer use metacity and it will not work anymore. If I use synaptic to uninstall every package and do a reinstall of beryl without emerald I will be unable to get it to work again unless I reinstall ubuntu. I would really appreciate some help. 

thank you,

gecko94:KS

Hi could you give us some specs on your system? I had this happen to me on a laptop and I could on conclude that it was the lack of memory because when I upgrade the memory it stop.

---

### Post by gecko94 on 2007-08-10
sure! these are my specs:
2.0 Ghz p4 proc.
512 Mb DDR RAM
IBM netvista series MoBo
ATI Radeon 9200 Mac Edition (128 Mb DDR RAM) flashed to use pc 9200 series BIOS

---

### Post by overdrank on 2007-08-10
> **gecko94 said:**
> sure! these are my specs:
2.0 Ghz p4 proc.
512 Mb DDR RAM
IBM netvista series MoBo
ATI Radeon 9200 Mac Edition (128 Mb DDR RAM) flashed to use pc 9200 series BIOS

Ok I had a Ati 9200 and it worked great for me. But that doesn't mean anything with computers. Ok which version of ubuntu are you using, Feisty, Edgy? And have you tried compiz-fusion yet
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
It is a little more stable but I do run beryl on some of my systems. I would try to remove Beryl and Emerald and then reinstall again through the command line
```
sudo apt-get remove beryl beryl-manager emerald-themes
```

and then use the same command except for install to replace remove of course.

---

