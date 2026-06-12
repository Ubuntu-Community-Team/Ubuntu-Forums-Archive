---
title: "options for kde/gnome in splash screen missing"
date: 2008-11-04
forum: Desktop Environments
---

### Post by SteveNorman on 2008-11-04
I just installed kde on top of ubuntu. When I reboot, I noticed that my options menu is mising from my splash screen. In a related issue, my splash screen is not in the correct resolution. My resolution should be 1440x900

what I tried:
 ```
~$ sudo update-initramfs -u
```

no noticeable effect

```
sudo gedit /etc/usplash.conf

changed to:
# Usplash configuration file
xres=1440
yres=900


```

```
sudo gedit /boot/grub/menu.lst file

added vga =789 to 
## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash vga=789
initrd          /boot/initrd.img-2.6.24-21-generic
quiet
```

My logic being that if the splash screen is the wrong resolution, the menu may be out of sight. I added the vga option with the number as i could not fignd the correct code for my screen. Since this code was for a smaller screen I thought it would shrink the login splash to where the menus could be seen if they are just off screen. No such luck, as everything appears the same.
 I would like to be able to have the kde/gnome option available at cntrl-alt-backspace, and for my resolutions to be correct.

---

### Post by SteveNorman on 2008-11-04
quick update, I am restoring my settings as now the splash loading screen is off to the left to much. Also I see that hitting f10  at the login splash gives me the option to boot into kde. I would still like to know how to properly configure the splash et al for my resolution.

---

