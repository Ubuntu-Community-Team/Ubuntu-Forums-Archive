---
title: "Splash screen is not working for me"
date: 2009-06-02
forum: General Help
---

### Post by Graf+ on 2009-06-02
Here is my /boot/grub/menu.lst file:
```

default        0

timeout        3


## ## End Default Options ##
title        Ubuntu 8.10, kernel 2.6.24-21-generic (3.2 Gb RAM)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=3bdc783a-1c86-45b8-9fe2-9f9c11be4ca2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-server (4 Gb RAM)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-server root=UUID=3bdc783a-1c86-45b8-9fe2-9f9c11be4ca2 ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-server
quiet


title        Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=3bdc783a-1c86-45b8-9fe2-9f9c11be4ca2 ro single
initrd        /boot/initrd.img-2.6.24-21-generic


title        Ubuntu 8.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title        MCBC 3.0
root        (hd0,1)
chainloader    +1

title        Windows XP Service Pack 3
root        (hd0,2)
chainloader    +1



##END DEBIAN AUTOMAGIC KERNELS LIST
```Looks like I should see a splash screen on boot, but quite opposite I see a black screen with running strings (details about boot process, like "* Starting NTP server ntpd" and so on).
The most annoying thing is that every 37th time I boot, disk check is forced and I can't dismiss it by pressing escape. 
I have an idea what some packages are missed, that's why splash screen is not working for me, menu.lst seems to be correct.
What should I do?

---

### Post by Legace on 2009-06-02
First, enter the command below into terminal, and make sure the X and Y values are correct.
```
gksudo gedit /etc/usplash.conf
```

Next, type in the following:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Reboot, and it usplash should appear :)

---

### Post by plucky on 2009-06-02
> **Legace said:**
> First, enter the command below into terminal, and make sure the X and Y values are correct.
```
gksudo gedit /etc/usplash.conf
```

Next, type in the following:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Reboot, and it usplash should appear :)

@Legace

Are you sure?

What does your usplash.conf contain?

Should not the first command be "open a terminal window"?

Just thinking aloud

---

### Post by Legace on 2009-06-02
> **plucky said:**
> What does your usplash.conf contain?
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1440
yres=900
```

> **plucky said:**
> Should not the first command be "open a terminal window"?

*"First, enter the command below into **terminal** --"*

---

