---
title: "DPKG error"
date: 2008-12-11
forum: General Help
---

### Post by Thura on 2008-12-11
After I unistalled usplash ... I got an error in synatic ...

`sudo apt-get install -f` is not working either ....

This is my output from dpkg --configure -a

```
thura tmp :sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27.8
Cannot find /lib/modules/2.6.27.8
update-initramfs: failed for /boot/initrd.img-2.6.27.8
dpkg: subprocess post-installation script returned error exit status 1

```

What's wrong ?
I currently have only two kernels installed 2.6.27.9 and 2.6.24.21 
Why is it trying to generate for 2.6.27.8 ? :confused:
Whoops any idea ?

---

### Post by Thura on 2008-12-11
Now, it is solved ...
I downloaded usplash using http, reinstalled and removed again ...

---

