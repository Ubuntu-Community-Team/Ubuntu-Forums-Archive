---
title: "non-SMP kernel required"
date: 2009-04-03
forum: General Help
---

### Post by KDJayde on 2009-04-03
Hello, I am having trouble with installing a specific client to connect to my school's VPN network. Unfortunately, the school does not provide information about the VPN server so using a different client is not an option. They say that "the client needs a 2.4.x kernel or a 2.2.12 or greater kernel. It does not work with the 2.5 kernel series kernels or SMP (multiprocessor) kernels." I am using Ubuntu 8.10 with kernel version 2.6.27-11.

Here are their instructions.
1)As root, untar the gzip'd tar file (tar xzvf).  This will create a directory called vpnclient. 
2)Go in to the vpnclient directory and type ./vpn_install.
3)If you want the vpn driver module loaded at boot time, answer 'y' to that question.
4)Accept the defaults for all the others.

I have gone as far as step two. When I type "./vpn_install" in the vpnclient directory, nothing happens. I'm assuming this is because I am running an SMP kernel.

I've tried running the 2.6.27-11 kernel with "nosmp." This did disable one of the cores of my dual core processor (veried by cat /proc/cpuinfo). I've also tried it with maxcpus=1. None of these steps work.

Does anyone have any suggestions on how I may be able to get this to install? My idea is to add a non-SMP kernel to the boot menu and load to that every time I need to work through the VPN but maybe there is a simpler way. If this is the only way, which kernel could I use and how would I go about having Ubuntu recognizing it? I understand this may be a little complicated but I am willing to learn :).

---

### Post by sdennie on 2009-04-03
Without seeing the vpn_install script, I can't say for sure but, my guess is that it's trying to compile a kernel module that was written for the 2.4/2.2 series of kernels.  In which case it will probably never work in a 2.6 kernel and probably won't work in any recent distro.  As insane as it sounds, the only way you are likely to accomplish what you are trying to do is to dig up some 5-10 year old linux distro and use that.  It's possible that you could build a 2.4 kernel and try to run it with Ubuntu but, I've never tried that and I don't know if it will work (it probably won't).  In fact, both of the methods I just suggested probably won't work on modern hardware because the kernels won't recognize any of the hardware.

---

