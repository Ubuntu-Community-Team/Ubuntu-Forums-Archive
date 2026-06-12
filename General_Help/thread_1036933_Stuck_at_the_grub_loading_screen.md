---
title: "Stuck at the grub loading screen"
date: 2009-01-11
forum: General Help
---

### Post by supremedalek on 2009-01-11
I have here a IBM Thinkpad 390E (A P2 laptop with really nice keyboard) running xubuntu. Last night I let it update itself (not using apt-get but the app that pops up when it tells it wants to upgrade).  When I rebooted it, this is as far as it went:

```
GRUB loading stage 1.5

GRUB loading, please wait...
Press `ESC' to enter the menu... 2
```

I would have expected "2" to count down to 0 and then it would pick the default kernel and run with it. I checked /etc/menu.1st and it does have timeout set to 3 seconds, so I would that countdown to take, well, 3 seconds and then boot as usual (also told it to hide the kernel menu). But, it does not. It just stays there frozen. Now, if I press the Esc key, I am provided with the list of available kernels. By selecting the one I want, it boots up as business as usual. 

What am I missing here?

---

### Post by taurus on 2009-01-11
Check the entries in /boot/grub/menu.lst.  If you want to use the old kernel, just change the **default** from 0 to 2 or whatever entry your old kernel is.

---

### Post by supremedalek on 2009-01-11
I tried that before posting and it did the same thing. What annoys me is the countdown is not counting down to then going to the next step. It just stays there at "2."

The menu.lst file looks like this (comments removed):

```
default         0
timeout         3
hiddenmenu   

title           Ubuntu 8.04.1, kernel 2.6.24-23-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=4200c627-75c6-493b-b349-1dbae4ec55e5 ro quiet splash
initrd          /boot/initrd.img-2.6.24-23-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=4200c627-75c6-493b-b349-1dbae4ec55e5 ro single
initrd          /boot/initrd.img-2.6.24-23-generic

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=4200c627-75c6-493b-b349-1dbae4ec55e5 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=4200c627-75c6-493b-b349-1dbae4ec55e5 ro single
initrd          /boot/initrd.img-2.6.24-22-generic
```

---

### Post by taurus on 2009-01-11
You could reinstall grub to MBR again to see if that fixes it.

```
sudo grub-install /dev/sda
```

---

### Post by supremedalek on 2009-01-11
Just tried that; it did not work. :confused: It is still winning.

---

