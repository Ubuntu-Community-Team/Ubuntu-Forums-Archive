---
title: "Trying to customize the kernel..."
date: 2005-06-06
forum: Desktop Environments
---

### Post by nilus on 2005-06-06
Ok, my distro is Hoary 5.04 installed in a Acer TM 290.
I would like to reduce the time to turn on pc, so i decided to download the same kernel i had ( from [www.kernel.org](www.kernel.org) ) and then follow the guides found on the net.
The command are always the same.
After I run menuconfig I create bzImage and then i run make modules and then make modules_install.
In grub's menu.lst I added this:
> title		Linux kernel 2.6.10-flaz
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-flaz root=/dev/hda3 ro
savedefault
boot
Obviously the vmlinuz file and System.map are in /boot directory.

When I start Ubuntu with my modified kernel I got this error:
> Please append a correct "root=" boot option

I "googled" a lot and I lerant that usually this problem is caused by the file system support, wich is not installed or is not installed as "built-in". So I tryed to install as built-in ext2, ext3 and reisdefs (which wasn't useful for me) and I get the same error.
I "googled" again and I find some correct information about the settings of the IDE Controllers, also these must be installed as built-in ( Uh... but... in menuconfig most of these i can only [not instal]/[module]...)... I did also this... but the result is always the same.

I don't know why, but the error is not given immediatly after grub menu. It begin to load the kerel, and after a few seconds there is the error.

I tryed another kernel but is always the same story.
I tryed to run make oldconfig but is always the same story.
I also tryed to include /boot/.config in menuconfig but the error persists.

What can I do? Is there something worng in the procedure?

Thanks

---

### Post by nilus on 2005-06-06
Oh, i forgot, i also get (with the other error) a non-syncing error in VFS... I can't remember the message very well, but is something about mounting root directory...

---

### Post by scoon on 2005-06-06
Hey there, 

With 2.6 kernels, compiling commands that should be used after you create your .config are: 

1. make all
2. make modules_install
3. make install

It appears all you have done is make your modules and install them, but you never installed your kernel.  Also, in the root directory of the sources you downloaded is a file called README that will have more on this info. 

regards, 

scoon

---

### Post by az on 2005-06-06
It is easier to just make a package for your kernel image.

Install fakeroot and kernel-package.   Also, install linux-tree.  It is a better starting point because it contains a lot of patches, bugfixes and configuration you need for ubuntu.  You can make menuconfig and remove the options you do not need.

cd to the top of the linux tree and do

fakeroot make-kpkg --revision=1 --append-to-version=MyCustonKernel kernel_image kernel_headers

That will compile and build a kernel-image package that you can install with dpkg -i.  It is easier to install and remove that way.  It also guarantees that your system is not left unbootable (by not screwing up your bootloader and leaving you other options)

---

### Post by thom_raindog on 2005-06-06
I try to install the kernel sources / tree / headers for 2.6.10.5 (the kernel I use). since the nvidia-driver installer requests so. Mind you, I don't know a whole lot about that, which is why I don't know if there is any difference between tree/sources/headers and if so which.. anyhow..

I tried apt-get in about three dozen ways, all it did so far was install the sources for 2.4.27 as tar.bz2 (which has happened to others as I read in the forum) and a headers directory for 2.6.10.5. None of which satisfied the installer.. I have seen people pointing to a package named linux-tree-XXXX which seems like what I need but with my kernels version number I can not find one.. 
Of course I have updated apt and also put all possible repositories in my list..

any ideas?

---

### Post by az on 2005-06-06
[http://packages.ubuntu.com/hoary/devel/linux-tree-2.6.10](http://packages.ubuntu.com/hoary/devel/linux-tree-2.6.10)

That is what you need.

---

### Post by nilus on 2005-06-07
I found this commands in the Debian guide:

make menuconfig
make-kpkg clean
fakeroot make-kpkg --revision=custom.1.0 kernel_image
dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb
mkinitrd -o initrd.img-2.6.8.1 2.6.8.1

I tryed these... but I always have the VFS problem. Next time i will try exactly how is written in the README of the kernel. I'm getting crazy :eek:

---

