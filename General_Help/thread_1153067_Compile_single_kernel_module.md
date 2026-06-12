---
title: "Compile single kernel module"
date: 2009-05-08
forum: General Help
---

### Post by Cybermax on 2009-05-08
Is it possible to recompile a single module using the linux-source package for Ubuntu?

Details:
I am running Ubuntu Jaunty with the default 2.6.28-11-generic kernel (what is recomended installed when i upgraded).

Now, i need to patch a kernel module (mac80211.ko), so that i can use it with my broadcom network card. I do not need any hints on how to get wireless to work, cos i can get it to work with the restricted Broadcom STA driver, but i want to use it with the b43 module, and thus need a patched mac80211.ko module.

So.. how can i compile ONLY that module, and not have to compile a brand new kernel?

I have done the following:

Downloaded the "linux-source" package from the package manager. extracted it to /usr/src/linux-source-2.6.28 . 
I did the following : 
```
cp /boot/config-2.6.28-11-generic /usr/src/linux-source-2.6.28/.config
make oldconfig
make prepare0
make scripts
```

I then patched the mac80211 module and did:
```
make /usr/src/linux-source-2.6.8/net/mac80211/mac80211.ko
```

I copied the newly created mac80211.ko module into /lib/modules/2.6.28-11-generic/kernel/net/mac80211 folder

then depmod -a

then modprobe b43

The output is then:

```
WARNING: Error inserting ssb (/lib/modules/2.6.28-11-generic/kernel/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/b43/b43.ko): Invalid module format
```
dmesg output is:
```
[  266.525145] mac80211: no symbol version for struct_module
```

Now.. i have a sneaky suspicion that the "no symbol for struct_module" indicates that the module is compiled from a different kernel source than the currently running kernel.. But what can i do about that? Is the "kernel-source" package for Ubuntu Jaunty NOT the same version then? Is it possible to actually get the exact same version so that i can compile ONLY the module, and not have to do a lot of other stuff (dreadded make menuconfig with a gazillion options i am rather clueless about).

Hints?

C

---

### Post by Cybermax on 2009-05-09
So.. noone knows why i cannot compile kernel modules by using this source for Ubuntu Jaunty?

Is the "linux-source" package the correct version compared to my already running kernel?

C

---

### Post by hackerb9 on 2009-08-14
According to the Debian folks, you should be using the linux-headers package.  They've got a swell tutorial on compiling just a single kernel module here: [http://www.debian-administration.org/article/Rebuilding_a_single_kernel_module](http://www.debian-administration.org/article/Rebuilding_a_single_kernel_module)

By the way, I just tried it and it worked for me without copying the header-common files the tutorial mentioned.  Something like this will probably work for you, too:

```

$ sudo apt-get install linux-headers-`uname -r`
$ cd ~/mymodsrc/net
$ ls mac80211.c
mac80211.c
$ make -C /usr/src/linux-headers-`uname -r`  M=`pwd`  modules
$ sudo insmod mac80211.ko

```

--b9

---

