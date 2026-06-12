---
title: "Problems upgrading to 2.6.11"
date: 2005-05-24
forum: Desktop Environments
---

### Post by pixelboy on 2005-05-24
Hi Guys,

Im very new to linux and hope someone can help me.

I have installed Ubuntu 5.04 succsesfully and am loving it. I need to upgrade to 2.6.11 to support my DVB card and have had problems.

I have installed the linux 2.6.11-1-K7 image, headers, source and tree from Synaptic. (ive got a Athlon 2500+)

On reboot i was presented with extra options in grub to boot to 2.6.11-K7 but when X starts it fails to load the Nvidia module and I get returned to bash prompt. (still boots to 2.6.10-5 fine)

Im guessing I need to disable nvidia somehow but i really new to this.

Any help would be appreciated.

Thanks

---

### Post by kleeman on 2005-05-24
The nvidia card needs linux-restricted-modules package installed for the correct kernel. 2.6.11 is not supported unfortunately (and won't be according to the devs). If you are an adventurous newbie  :smile:  :smile:  :smile: you could go to the nvidia linux website and follow their directions for installing the nvidia driver on a custom kernel....

---

