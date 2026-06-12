---
title: "KERNEL PANIC after compiling kernel"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Matthai on 2005-11-15
Hi, I have the following problem on Ubuntu Breezy.

First, I istall Breezy and uncoment backports repositories.

Then I enter the following commands:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev

I install customized kernel source:

sudo apt-get install linux-tree

Unzip and link it:

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2

sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd /usr/src/linux

Install right version of gcc and "relink" it:

sudo apt-get install gcc-3.4

sudo rm /usr/bin/cpp
sudo ln -s /usr/bin/cpp-3.4 /usr/bin/cpp
sudo rm /usr/bin/g++
sudo ln -s /usr/bin/g++-4.0 /usr/bin/g++
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
sudo rm /usr/bin/gcov
sudo ln -s /usr/bin/gcov-3.4 /usr/bin/gcov
sudo rm /usr/bin/gccbug
sudo ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
sudo rm /usr/bin/i486-linux-gnu-g++
sudo ln -s /usr/bin/i486-linux-gnu-g++-3.4 /usr/bin/i486-linux-gnu-g++
sudo rm /usr/bin/i486-linux-gnu-gcc
sudo ln -s /usr/bin/i486-linux-gnu-gcc-3.4 /usr/bin/i486-linux-gnu-gcc
sudo rm /usr/bin/i486-linux-gnu-cpp
sudo ln -s /usr/bin/i486-linux-gnu-cpp-3.4 /usr/bin/i486-linux-gnu-cpp

Then I run xconfig:

sudo make xconfig

Go to the "Cryptographic options" and set them ON (all of them):

Compile kernel:

sudo make-kpkg clean
sudo make-kpkg –append-to-version-plus-crypto kernel_image modules_image

Install new kernel:

cd ..
sudo dpkg -i kernel-image-2.6.12-plus-crypto_10.00.Custom_i386.deb

After reboot I receive: KERNEL PANIC.

Reboot again in previos kernel and write:

sudo apt-get install initrd-tools
sudo mkinitrd -o /boot/initrd.img-2.6.12-9-386-plus-crypto

sudo gedit /boot/grub/menu.lst 

CHANGE menu.lst in the following way:

title		Ubuntu, kernel 2.6.12-plus-crypto 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-plus-crypto root=/dev/sda4 ro quiet splash
initrd		/initrd.img-2.6.12-9-386-plus-crypto
savedefault
boot

title		Ubuntu, kernel 2.6.12-plus-crypto (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-plus-crypto root=/dev/sda4 ro single
initrd		/initrd.img-2.6.12-9-386-plus-crypto
boot

After reboot I receive KERNEL PANIC again.

Any idea what else should I do?

---

### Post by nagilum on 2005-11-15
Are the cryptographic options all that you changed in 'make xconfig'? Then you either have to go through the other options to check if they are appropriate for your system or you can copy one of the /boot/config-<kernel-version> to /usr/src/linux/.config and run 'make oldconfig' to import the current kernel configuration.

---

### Post by Joe_lurker on 2005-11-15
Are there any messages output before the kernel panic?  Those would help solve the problem.

-Joe

---

