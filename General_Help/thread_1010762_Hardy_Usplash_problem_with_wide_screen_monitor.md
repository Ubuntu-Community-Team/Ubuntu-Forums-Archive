---
title: "Hardy: Usplash problem with wide screen monitor"
date: 2008-12-14
forum: General Help
---

### Post by kevin1 on 2008-12-14
I am running Hardy with an LG W2234S wide screen LCD monitor with native resolution of 1680 x 1050. When booting has finished the display is OK and at 1680 x 1050.

Initially while booting the monitor displayed an 'out of range' message instead of the usplash screen. I have modified the relevant entry in /boot/grub/menu.lst to include vga=791 after unsuccessfully trying many other values. 

Now the usplash screen displays, but the Ubuntu logo begins to the right of mid-screen with part of the 't' and the 'u' wrapped round to the left of the screen. The boot log text displays at the extreme bottom right, possibly with some lines off the bottom of the screen, and as the text scrolls up it corrupts the progress bar.

Can anyone suggest how to fix this?

Thanks,

Kevin

---

### Post by dexter on 2008-12-14
You can set the usplash resolution in /etc/usplash.conf. 
You should set it to the native resolution of your display.

---

### Post by kevin1 on 2008-12-14
Thanks for your reply, dexter.

This is the existing usplash.conf:

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1680
yres=1050
```

The resolution values are correct and were inserted in the file by the system, but presumably are not being applied. In case the problem is due to update-initramfs having not been executed automatically I have just done so manually, with the following result:

```
kevin@MainPC:~$ sudo update-initramfs -u -k 2.6.24-22-386
[sudo] password for kevin: 
update-initramfs: Generating /boot/initrd.img-2.6.24-22-386

```

I then rebooted, but the above had made no difference.

What should I try next?

Kevin

---

### Post by hopla on 2009-01-26
Kevin,

Try vga=0x369 in /boot/grub/menu.lst

---

