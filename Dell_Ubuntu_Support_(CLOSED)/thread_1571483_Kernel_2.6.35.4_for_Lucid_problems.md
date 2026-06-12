---
title: "Kernel 2.6.35.4 for Lucid problems"
date: 2010-09-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by snif123 on 2010-09-09
Hi all,
I have installed the newer kernel 2.6.35.4 and everything seems fine.I followed this tut,[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)
The problem I have is everytime I try to install anything,I get an error "bcmwl-kernel-source failed to install or upgrade"
The installation completes for the 2.6.32.24 generic kernel but fails for this newer kernel.
I have attached 3 screenshots showing the error message in more details hopefully.
Error message is shown very clearly in third attachment,sorry I couldn't manage to copy the error and paste it.
Cheers

---

### Post by sgosnell on 2010-09-09
Did you install the headers for the .35 kernel?

---

### Post by snif123 on 2010-09-10
HI
Am not sure what you mean whether I installed the headers?I only followed the tut I linked to word by word.
I have checked in /usr/src and there are only headers for the default kernel and another one 2.6.34...but this one I had installed by clicking deb files and not compile the source like the .35(I since deleted the .34)
Also I had the same exact error with the .34 as seen in the screenshot5 which is why I deleted it.

---

### Post by halj32 on 2010-09-10
Hi
I have the same problem with the 2.6.35.* kernels. there is a line on one of the configuration file is wrong (line 21 I think) but I cant find out what it should be 
/usr/src/bcmwl-5.60.48.36+bdcom/src/wl/sys
goodluck

---

### Post by halj32 on 2010-09-10
right Ive just been to broadcom site and you need to download & install 2 patches
sta_5.60.48.36_2.6.33_kernel_patch.zip
&
sta_5.60.48.36_2.6.34_multicast_kernel_patch.zip
extract to /usr/src/bcmwl-5.60.48.36+bdcom (as admin)
then in an terminal run 

sudo patch -p0 < patch
then
sudo patch -p0 < patch_hybrid_multicast

youll probably need to install dkms ect

then run
sudo dpkg --configure -a

reboot & done everything should be working

---

### Post by snif123 on 2010-09-10
Hi
I have executed your suggestion.
Thanks alot,howver the problem has persisted exactly as it was 
Am looking at the error
-----------------------------------
DKMS make.log for bcmwl-5.60.48.36+bdcom for kernel 2.6.35.4 (i686)
Fri Sep 10 14:26:22 BST 2010
make: Entering directory `/usr/src/linux-2.6.35.4'
  LD      /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o
In file included from /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.c:19:
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/include/linuxver.h:23:28: error: linux/autoconf.h: No such file or directory
make[1]: *** [/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-2.6.35.4'
I will try to have a look at the error **error: linux/autoconf.h: No such file or directory
cheers

---

### Post by sgosnell on 2010-09-10
You have to install two .deb files, one is the image, the other is the headers.  If you want to compile your own kernel, you must have the headers installed.  You don't need the headers for normal use, but you do for compiling the kernel.  You can get all the .deb files from [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/), by navigating to the proper kernel.

---

### Post by snif123 on 2010-09-13
Hi
Thanks alot,am back to work now.
I have tried to install the .deb for the headers but it gives dependency errors.
Also before,I tried the .34 kernel but that time I downloadded the .deb files for the headers and image and installed them following a tut. on web.I got the same same situation am in at the moment which is why i opted to compile the code approach.:?

---

### Post by sgosnell on 2010-09-13
All the dependencies should be available on the same page.  There is more than one header .deb.  IIRC, you have to install both, in a specific sequence.  I don't recall offhand which is which, because I never bother to install them, since I don't compile my own kernel.

---

### Post by Djhg2000 on 2011-01-20
Sorry for bumping, but it looked like he never found any solution and I think this is something important which more developers need to be aware about.

The source of the problem is that since around 2.6.33 autoconf.h moved from linux/ to generated/ in the source tree, along with some other headers such as the more famous utsrelease.h.

I guess you could symlink autoconf.h as a temporary solution, but I'd suggest filing a bug report if the problem still exists.

I'm on Debian so I can't verify it right now, but this *should* work for you until the bug is fixed:
```
cd /usr/src/linux-headers-2.6.34*/include
ln -s generated/autoconf.h linux/autoconf.h
```

---

