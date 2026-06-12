---
title: "picture cut off"
date: 2006-09-19
forum: Desktop Environments
---

### Post by umbepo on 2006-09-19
Hello,

I am runinng ubuntu 6.06.1 with kernel 2.6.15-27-386.

Intel P4 Prescott 3.2 ghz w/ht
250GB ATA hd
1gb ddr2 memory
Sound Blaster Live! 64-bit sound card
nVIDIA XfX 7300gs PCI-e 256mb gpu


My screen in ubuntu *only* (dual booting with xp) is slightly shifted to the right. In other words, the left side of the screen has about half an inch of black and the right side is cut off half an inch. I am running a 19" LCD monitor thru VGA. The screen is cut off first at the ubuntu login screen, as I cannot tell thru the boot.

When I change the resolution, the problem persists.

Thanks!

---

### Post by umbepo on 2006-09-19
Arr! I fixed it meself.

Just had to install drivers. Silly me :tongue: 


sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable


That's it for anyone in the future.

---

