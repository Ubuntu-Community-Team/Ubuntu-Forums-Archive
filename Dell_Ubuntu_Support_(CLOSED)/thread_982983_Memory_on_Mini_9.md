---
title: "Memory on Mini 9"
date: 2008-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yvinogradov on 2008-11-15
Hi, I bought a Mini 9 with Ubuntu and an upgrade to 1G of memory, but when I open System Monitor it reports the amount of memory as 883.2M. Does anybody know why? Thanks!

---

### Post by armandh on 2008-11-15
some devoted to the video????
just a guess

---

### Post by yakker.yak on 2008-11-15
Yes, up to 64 MB will be devoted to the video, which as in many laptops is of the integrated variety (Intel GMA 950).

---

### Post by cmspider on 2008-11-16
This is actually because the kernel was compiled without highmem support.

I compiled my own kernel from ubuntu's sources, and now free shows
1025056 k total memory.

This wasn't particularly easy though - if you haven't built kernels on other systems before...

---

### Post by wx0112 on 2008-11-16
> **armandh said:**
> some devoted to the video????
just a guess

I upgrade memory to 2GB and encounter the same problem. Did you believe such large video memory?

---

### Post by starcannon on 2008-11-16
> **cmspider said:**
> This is actually because the kernel was compiled without highmem support.

I compiled my own kernel from ubuntu's sources, and now free shows
1025056 k total memory.

This wasn't particularly easy though - if you haven't built kernels on other systems before...

Ah-ha-ah, good grief Dell, come on guys.

Thanks for the heads up cmspider, I know what I'll be doing shortly, just ordered 2gb of ram from newegg, kinda pointless without the kernel. I'm a bit astounded that option was overlooked in the kernel configurator for these things. /sigh.

---

### Post by 2damncommon on 2008-11-16
> **cmspider said:**
> This is actually because the kernel was compiled without highmem support.

I compiled my own kernel from ubuntu's sources, and now free shows
1025056 k total memory.

This wasn't particularly easy though - if you haven't built kernels on other systems before...
I have been waiting to see someone post this.
When I attempted it I got ARCH and SUBARCH errors I did not know how to resolve.
Did you get them too? If so how did you resolve them?

---

### Post by cmspider on 2008-11-18
I built my kernel the vanilla way:

working from memory as to what I did: (don't attempt if you can't sanity check what's here, this is potentially system-borking stuff)

I used apt-get linux-sources 
to download the kernel source (which appears to be not quite exactly the same as was used to build the binary that shipped, but pretty close...)
then as root:

cd /usr/src
tar -jxvf linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24
cp /boot/config-2.6.24-19lpia .config
make oldconfig
make menuconfig (turn on the HIGHMEM option then exit and save)
make
make modules_install
cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.24.3
cp .config /boot/config-2.6.24.3

cd /lib/modules
cp -r 2.6.24-19lpia/volatile 2.6.24.3/
cp -r 2.6.24-19lpia/ubuntu 2.6.24.3/
update-initramfs -k 2.6.24.3

then edit /boot/grub/menu.lst and at the very bottom add a stanza for the new kernel, I'd also suggest increasing the delay time to something greater than 0 so you leave the stock kernel as the default, but select the new one from the grub menu till you know it works.

good luck.

---

### Post by 2damncommon on 2008-11-20
Thank you for your post cmspider.

It is pretty similar to the Ubuntu kernel build instructions using kpkg that failed for me.

You have a few more typos; **cd linux-source-2.6.24**; **cp -r 2.6.24-19-lpia/volatile 2.6.24.3**; **cp -r 2.6.24-19-lpia/ubuntu 2.6.24.3**.

I skipped "make oldconfig" and chose the option at the bottom of make menuconfig to use a different config file.

The kernel boots and shows the full 2GB of RAM with "free -m" but my wireless is not recognized.

---

### Post by cmspider on 2008-11-20
Is the wl module loaded?

you can try: modprobe wl

and see if works.  You might need to do a depmod -a
If the modprobe works and the module doesn't get loaded automatically after the depmod, you can try adding it /etc/modules

---

### Post by 2damncommon on 2008-11-20
> **cmspider said:**
> Is the wl module loaded?

you can try: modprobe wl

and see if works.  You might need to do a depmod -a
If the modprobe works and the module doesn't get loaded automatically after the depmod, you can try adding it /etc/modules
Not only is the wl module not loaded, a line count of lsmod shows the default lpia kernel has 77 lines and the new kernel has 56 lines.

Yes. "depmod -a wl"; "modprobe wl", works great. Wireless is now connected.

EDIT-Here is "free -m":
             total       used       free     
Mem:          2017        483       1533

EDIT2:
I am guessing a "depmod -a" is required. After running that I see 75 lines on lsmod for the new kernel.

---

