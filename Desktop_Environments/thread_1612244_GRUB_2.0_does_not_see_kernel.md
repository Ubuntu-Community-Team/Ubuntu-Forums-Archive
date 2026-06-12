---
title: "GRUB 2.0 does not see kernel"
date: 2010-11-02
forum: Desktop Environments
---

### Post by djm0001 on 2010-11-02
I am new to kernel compilation and have struggled a little bit during the process, so please keep that in mind, but I believe I have done everything right except when i run sudo update-grub, my new kernel is not detected. I am running Ubuntu 10.04 w/ GRUB 2.0.

I followed this tutorial on compiling your own kernel:
[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html) , it worked out alright but I have noticed that most tutorials vary and it can be somewhat confusing as to what the correct way is. 

Anyway, I made it all the way to the end without any errors, however when I attempt to update the GRUB menu, my new kernel simply does not show up. Unfortunately, I really don't know what information to post here so let me know what would help out. It's been very frustrating and i apologize if there is already a thread for this, please link if there is. thanks

---

### Post by karmila on 2010-11-03
Maybe first you can check if the kernel is already installed or not from synaptic.

---

### Post by hepata on 2010-11-03
Same problem here [[img]http://www.useflat.de/img/s13.gif[/img]](http://www.useflat.de/).. the new custom kernel just won't appear. What could be the cause :confused:

---

### Post by djm0001 on 2010-11-03
It is not already installed, nor does it show up in the GRUB boot menu when I hold <SHIFT> on startup, sudo update-grub returns the two other kernels (initrd and vmlinuz files for both) just fine, mine however do not show up. I also tried making them executable as I read update-grub will only search for executable files, still to no avail.

---

### Post by mike_f on 2010-11-03
Ahh, more reasons to fuel my dislike of GRUB2.

Just for a sanity check, did you try hardcoding a new menuentry in /etc/grub.d/40_custom just for testing? Something like:
```
menuentry 'Test kernel'{ 
 insmod ext2
 set root='(hd0,1)'
 linux /boot/vmlinuz-whatever root=/dev/sda1 ro
 initrd /boot/initrd-whatever
}
```

---

### Post by djm0001 on 2010-11-05
> **mike_f said:**
> Ahh, more reasons to fuel my dislike of GRUB2.

Just for a sanity check, did you try hardcoding a new menuentry in /etc/grub.d/40_custom just for testing? Something like:
```
menuentry 'Test kernel'{ 
 insmod ext2
 set root='(hd0,1)'
 linux /boot/vmlinuz-whatever root=/dev/sda1 ro
 initrd /boot/initrd-whatever
}
```


No, I have not tried that. I read about changing that file but didn't want to screw around with too many things, I'll give that a try and see if it works. Thanks for the suggestion. 

Just out of curiosity, since you said this fuels your dislike for GRUB2, do you know why this happens or what problems in GRUB2 could lead to this? Unfortunately, I don't fully understand kernel building/the boot loader and what each step is actually doing, so its hard to debug when the process doesn't work as expected. Again, thanks for the help

---

### Post by djm0001 on 2010-11-08
It worked.

By adding the manual entry it shows up in the boot menu at startup. The kernel still does not show up by using sudo update-grub, so I guess I'll just have to manually update it. Thanks for all the help

---

