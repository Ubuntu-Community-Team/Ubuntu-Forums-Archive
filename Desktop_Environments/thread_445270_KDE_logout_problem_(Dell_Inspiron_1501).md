---
title: "KDE logout problem (Dell Inspiron 1501)"
date: 2007-05-15
forum: Desktop Environments
---

### Post by Caligula on 2007-05-15
I've just installed kubuntu feisty on a brand new dell machine. Now everytime I logout of kde I just get a black screen of which there's no way to get out of except manually turning the computer off.

I know it's a common problem on this laptop, and I know the way to get rid of it in gdm (checking "restart Xserver after each login"), but since I use kdm that doesn't help me that much :/

Anyone knows something?

Thanks,
Josh

---

### Post by thayerw on 2007-05-16
Have you tried adding vga=791 to your linux command line in the grub configuration?  I know this works for folks suffering from garbled text when switching runlevels, but it may help you as well.

Edit the config file:

```
kdesu kate /boot/grub/menu.lst
```

Now look for the kernel command line...something like this:

```
## ## End Default Options ##

kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=41a05604-9d2b-4e55-986d-bf14842dabd7 ro quiet
```

Add vga=791 to the end, so it looks like this:

```
## ## End Default Options ##

kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=41a05604-9d2b-4e55-986d-bf14842dabd7 ro quiet vga=791
```

If that works, you might want to add the command to your default options (found earlier in the same file) so it will automatically append the command to any new kernels:

```
# defoptions=quiet vga=791
```

---

### Post by argux on 2007-05-22
I have the same laptop, and I used to have that very same problem. It was actually X who was crashing. I don't remember exactly how I caused it, but I'm pretty sure it had to do with using the official ATI drivers. Did you change anything about that in your xorg.conf?

If so, change back the driver to 'ati' and, if you really want to have 3D acceleration, use the instructions from the wiki, which helped me. Now I have 3D acceleration and no crashing, thought I haven't tried hibernation or suspend.

---

### Post by Caligula on 2007-05-23
It was actually happening only with the official ATI drivers.

I've installed the fglrx driver direct from ATI (not with restricted-manager), but it causes loads of problems, DVDs are coming up as a blurry picture, only in VLC do they show properly, but also with bad quality, openGL rendering doesn't work anyway, and the computer sometimes doesn't turn on/off, and all kinds of weird problems.

With what guide exactly did you install fglrx?

---

### Post by linux-warrior on 2007-06-20
I'm having instability problems when login out on an Inspiron 1501 with the official Ati driver 8.37.6 (Kubuntu)
Sometimes it just hangs sometimes it gets back to the login screen but the display is garbled,
Any help ?

---

