---
title: "No boot splash screen on Edubuntu 8.10"
date: 2009-03-27
forum: General Help
---

### Post by Rainbow Road on 2009-03-27
I have installed Edubuntu 8.10 on 2 computers and Edubuntu 8.04 on another (couldn't get Ubunutu 8.10 to install on this one). Since installing the boot and shutdown process is now text only rather than displaying the graphical splash screen on the 8.10 computers (the 8.04 computer has changed from displaying the Ubuntu Splash to the new Edubuntu). I have tried to reinstall the edubuntu-artwork-usplash from the CD but it still doesn't work.

I have found the following information on another website to change the splash screen to a different one by choice. Both computers are dual booting with XP so I don't want to totally corrupt the boot process.

> 1. firstly get the available splash screens. Do a
sudo apt-get install usplash*
It will display a list of available splash screens with ubuntu.
2. Next check out the available splash screens in /usr/lib/usplash
ls -lh /usr/lib/usplash
total 12M
-rw-r--r-- 1 root root 43K 2006-11-23 17:42 debian-edu-usplash.so
-rw-r--r-- 1 root root 2.3M 2007-03-30 17:33 edubuntu-splash.so
lrwxrwxrwx 1 root root 36 2007-05-17 23:20 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
-rw-r--r-- 1 root root 2.0M 2006-10-17 15:13 usplash-theme-ichthux.so
-rw-r--r-- 1 root root 2.3M 2007-04-07 15:36 usplash-theme-kubuntu.so
-rw-r--r-- 1 root root 2.6M 2007-04-10 18:28 usplash-theme-ubuntu.so
-rw-r--r-- 1 root root 2.0M 2007-03-19 16:17 usplash-theme-xubuntu.so
Here you can see that you have 6 splash screens and one soft link. Check out the softlink.
ls -lh /etc/alternatives/usplash-artwork.so
lrwxrwxrwx 1 root root 41 2007-06-29 08:38 /etc/alternatives/usplash-artwork.so -> /usr/lib/usplash/usplash-theme-xubuntu.so
It points back to one of the screens from the /usr/lib/usplash directory. So to change the screen simply change the soft link
sudo ln -sf /usr/lib/usplash/usplash-theme-kubuntu.so /etc/alternatives/usplash-artwork.so
And now check the new link
3. reconfigure the linux image
sudo dpkg-reconfigure linux-image-
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
.
.
Updating /boot/grub/menu.lst ... done
Thats done...
To check the new screen, no dont reboot simply type in
sudo usplash
And you can see the new screen - bingo. To get back to your xwindows environment press CTRL-ALT-F7


Do you think this would work, or has anyone any experience of this issue with Edubuntu 8.10 already?

I am still quite new to this so please don't be too technical.

---

### Post by blazemore on 2009-03-27
It will work. The worst that will happen is that your pretty graphic will be replaced by a black screen, or scrolling text.

---

