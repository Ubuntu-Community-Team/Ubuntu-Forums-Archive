---
title: "Kernel update and Grub (Error 15)"
date: 2009-02-25
forum: General Help
---

### Post by Zilioum on 2009-02-25
Hi!

A few days ago my kernel was updated from 2.6.27-07 to 2.6.27-11 and yesterday to 2.6.27-12. 
Now here's the problem: If I want to boot with the newest Kernel ...-12 I get the error message: File not found (Error 15)
Booting from ...-11 still works perfectly. 

So how can I fix error 15? 

And I also have a general question: What is the difference between these kernels? Does it make a big difference which I use?

Thanks for your help!

---

### Post by smani on 2009-02-25
You should be able to figure out the problem by looking at the grub configuration file - /boot/grub/menu.lst. Scroll to the bottom, there you will see a list of the kernels included in the boot menu. The important lines are the "kernel" and "initrd" lines, i.e. in my case:
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=6fe1d724-cd0e-4e68-bba0-14ecbc1742e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
Now check, do those files exist? Did the UUID of the harddrive change for whatever reason? (you can compare them with those listen by the blkid command). If everything seems okay, you could try with
```
sudo update-grub
```

Otherwise I guess something went wrong when updating the kernel, and the issue would require some further investigation.

New kernels usually fix problems and add features, though the latter mainly in major releases, say from 2.6.27 to 2.6.28. But if your system was already working fine, you may not notice any difference.

Note: clearly, caution when editing the menu.lst file;)

---

### Post by caljohnsmith on 2009-02-25
How about posting the output of:
```
cat /boot/grub/menu.lst
ls -l /boot
```
And we can work from there if you want.

---

### Post by Zilioum on 2009-02-26
I had a look at the menu.lst file. Couldn't find anything that looks weird. Didn't try the update command yet (altough I reinstalled grub from the live cd, didnt change anything), I'm at work and using xp :rolleyes: but I mailed myself a copy of my menu.lst file. so here are the two first kernels, the first one doesnt work, the second one does. (If you need more from the menu.lst, pls tell me.)

title		Ubuntu 8.10, kernel 2.6.27-12-generic
uuid		d595917a-5156-478a-b808-5294ca6adc68
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=d595917a-5156-478a-b808-5294ca6adc68 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
uuid		d595917a-5156-478a-b808-5294ca6adc68
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=d595917a-5156-478a-b808-5294ca6adc68 ro  single
initrd		/boot/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		d595917a-5156-478a-b808-5294ca6adc68
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d595917a-5156-478a-b808-5294ca6adc68 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d595917a-5156-478a-b808-5294ca6adc68
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d595917a-5156-478a-b808-5294ca6adc68 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

Caljohnsmith, if you still need those outputs, I'll post them as soon as I get home :) 


Thanks for your help!

---

