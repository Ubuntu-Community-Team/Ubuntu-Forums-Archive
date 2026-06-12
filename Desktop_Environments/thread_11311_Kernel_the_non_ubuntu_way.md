---
title: "Kernel the non ubuntu way?"
date: 2005-01-15
forum: Desktop Environments
---

### Post by relux on 2005-01-15
First off, a little background.  I am running Hoary and I do not have broadband.  I use my cell phone as my dedicated connection.  This is one of the reasons why I do not to use the ubuntu kernels.  I want to be build my own kernel and modules and install them myself.  I am familiar with all that.  How can I keep the current 2.6.9 kernel pinned at where it is? During dist-upgrades it tries to download 2.6.10 which is a huge download for me.  I also can not use the 2.6.10 kernel because of some broken usb driver issues.  It is pointless for me to download this for that reason also.  I would normally just apt-get remove the kernels and not use them but right now I do not have the 2.6.9 kernel source tree on my machine to build my kernel so I need to use the ubuntu one for now.  

How can I stay at 2.6.9 and not download 2.6.10 during dist-upgrades?

Thanks!

---

### Post by HankB on 2005-01-16
You might find what you need in the APT HOWTO:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

HTH,
hank

---

