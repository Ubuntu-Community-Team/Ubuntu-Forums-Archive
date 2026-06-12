---
title: "Kubuntu 8.04 won't start up"
date: 2008-07-12
forum: Desktop Environments
---

### Post by monnick on 2008-07-12
Today I installed Kubuntu 8.04 on my computer. I've installed it as an experimental distro, I use Ubuntu 8.04 as my primary OS. After the installation of Kubuntu I tried to boot it, but when I try the boot process gets stuck at the following line:

**Running local boot scripts: /etc/rc.local        [OK]**

I've searched on google and it looks like some other people have this problem too, but I cant find a solution. This problem may be caused by my graphic card, a ATi RADION x800 SE which is not supported by Kubuntu / Ubuntu by default. On Ubuntu I can only run de low-graphic mode, but when I install the *fglrx* drivers it works fine.

But I am not able to try to install these drivers in Kubuntu since my (USB) wireless network adapter is also not support by default, I've to use ndiswrapper to get my internet connection up.

I've tried to boot Kubuntu in recovery mode, but that doesnt work because I got into a terminal / console screen where I can do nothing.

I hope someone can help me with this annoying problem, it may be a temporary solution so I can install ndiswrapper and the fglrx drivers and then try again.

Thanks in advance! :)

---

### Post by jrd on 2008-07-13
When you get in the console type "sudo apt-get install fglrx".

This should get your card working.

---

### Post by monnick on 2008-07-13
No, because I don´t have internet because ndiswrapper needs to be installed as well.

---

### Post by jrd on 2008-07-13
Sorry...Didn't read that part. In that case you can just use the vesa driver to get booted up and then install the ones you need. When you get to the shell type "sudo nano /etc/X11/xorg.conf" and add vesa as the driver to use.. like this          ```
Section "Device"
Driver "vesa"
```

Let me know how it goes.

---

### Post by monnick on 2008-07-13
Woooh! Thank you very much, that did the trick!

Now I can finally explore Kubuntu, my first impression is very good. It looks very nice and the welcome sound is alot better than Ubuntu's one.

Now I only need to fix my internet, but that wont be that hard I hope. :)

Thx again!

---

### Post by jrd on 2008-07-13
You're welcome. Glad I could help.

---

