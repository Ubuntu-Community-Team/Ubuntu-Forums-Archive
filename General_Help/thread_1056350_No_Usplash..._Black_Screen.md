---
title: "No Usplash... Black Screen"
date: 2009-01-31
forum: General Help
---

### Post by icanfly0307 on 2009-01-31
Hi,
   I did a minimal install of Ubuntu and added gnome-core on top of it. I've also installed usplash and usplash-theme-ubuntu. However, whenever I boot, I get a plain black screen. My computer loads, but I don't see the splash screen. One thing that I've noticed is that usplash works if I install gnome with "apt-get install ubuntu-desktop" but not with the minimal install. Does anyone know how I can get the splash screen back? Thanks. :)

---

### Post by lavinog on 2009-02-05
Can you post your /boot/grub/menu.lst file?
There is a command that should be listed on the kernel line for enabling splash:

example: (don't copy this, it is from an old config)
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=be6707d2-4966-4651-8bae-3c4e5f228c36 ro splash

```

there is a program called startup-manager in the repositories that is a gui way of editing the boot config. There is an option to enable the splash

---

