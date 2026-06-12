---
title: "Howto: upgrade your kernel to 2.6.29 in 8.10"
date: 2009-03-27
forum: General Help
---

### Post by jonberling on 2009-03-27
Hello Everyone. 

On my machine I have an onboard Intel video card. The new kernel makes a big difference with Intel video cards. Here is instructions on how to install it. (Of course you can always wait until Ubuntu 9.10 comes out ;) )

First you need to install the package build-essential
```

sudo apt-get install build-essential

```

Next, you need to get wireless-crda, which isn't in the repositories. (If you're using 9.04 beta, skip this step, you already have it.)

32 bit
```

wget http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_i386.deb

```

64 bit
```

wget http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_amd64.deb

```

Now you need to get the kernel

32 bit
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb

```

64 bit
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_amd64.deb

```

Now that you got all of the files, you're ready to install!

```

sudo dpkg -i wireless-crda_1.7_*.deb
sudo dpkg -i linux*.deb

```

Once that is done, reboot your system and you should be good to go!


Thanks to the following sites for their help:
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)
[http://karuppuswamy.com/wordpress/2009/03/11/howto-update-ubuntu-with-latest-kernel/](http://karuppuswamy.com/wordpress/2009/03/11/howto-update-ubuntu-with-latest-kernel/)

---

### Post by IsmailBhai on 2009-03-27
thanks for the tut.

---

### Post by wisewomcat on 2009-04-15
When I upgraded to 2.6.29, my network randomly started dying (couldn't even ping localhost).  This was a known bug in 2.6.29...so you should probably install the patch 2.6.29.1.  The commands remain similar...you just have to update the files you get...

For 32 bit:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-headers-2.6.29-02062901_2.6.29-02062901_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-headers-2.6.29-02062901-generic_2.6.29-02062901_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-image-2.6.29-02062901-generic_2.6.29-02062901_i386.deb
```

For 64 bit:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-headers-2.6.29-02062901_2.6.29-02062901_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-headers-2.6.29-02062901-generic_2.6.29-02062901_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/linux-image-2.6.29-02062901-generic_2.6.29-02062901_amd64.deb
```

All of the other commands should be the same and still work.

---

### Post by keypox on 2009-04-15
whats the danger in this? 

I have my laptop running nicely but it does run intel graphics.  Should I just wait for the RC of 9.04 tomorrow?

---

### Post by wisewomcat on 2009-04-16
I tried doing the beta 9.04 upgrade, and eventually went back to 8.10.  The main issue I had was that the gnome-terminal program wouldn't start...which you can fix that by mounting a devpts filesystem.

The only other thing I didn't like is that my network connection was the last thing to activate...so any other program I wanted to start up when gnome launched would say "No internet connection."  Realistically, that's probably pretty easy to fix...and even if you don't, how often do you reboot your computer?

Oh, and they might have even fixed these issues in the release candidate...so who knows.  I'm personally going to wait for the final version of it.  (But I did make a separate /home directory on this last reinstall!)

This kernel upgrade was seemless though (after the initial trouble with the 2.6.29 version...the 2.6.29.1 version was perfect).  This kernel seems to boot much faster, and I haven't noticed VLC flickering when I'm scrolling in other windows.  If you do need to remove it for some reason, just uninstall the packages with the dpkg command (it's something like -r or -P for remove/purge).

```
dpkg -P {package name}
```

Really the only hard part is figuring out the package name...and I'm sure someone could tell you a better way of doing that.  What I did was just try different variations of the original file name, like linux-headers-2.6.29-02062901_2.6.29, or linux-headers-2.6.29-02062901 or linux-headers-2.6.29-02062901_2.6.29-02062901 (I'm just removing or adding to the end there).

---

### Post by loomsen on 2009-04-27
> **wisewomcat said:**
> 
Really the only hard part is figuring out the package name...

So, why would you need the packagename? 

@topic:

For me, running the generic configurations without any changes, 30-rc3 performs a lot better. 29-1 still causing pretty high CPU loads, my laptop just switched off a couple of times running 2.6.29-1 (usually during load intensive tasks tho, like compiling. 

Pretty annoying, as there won't be any log file, crashdump or so to trace back.

However, the kernels don't have reasonable defaults imo, so if you choose to keep one installed, you'd maybe want to rebuild it against your local apps and have your old kernels config as a base.

Then just consider whether to enable KMS/BTRFS/IPv6 or not.

So some slight configurations should be fine (like disabling debug messages where you don't need them).

So, all together, if you wanna keep it, build it, or at least review it's configuration to avoid bad surprises...

---

