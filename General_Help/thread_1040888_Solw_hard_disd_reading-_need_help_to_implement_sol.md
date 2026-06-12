---
title: "Solw hard disd reading- need help to implement solution"
date: 2009-01-16
forum: General Help
---

### Post by JulianLx on 2009-01-16
I'm using 8.04. After updating my system a month ago both of my IDE hard disks started to show very a slow performance.
After searching forums and bug reports, I came across this possible solution found here [http://linux-ata.org/faq.html#combined]("http://linux-ata.org/faq.html#combined")

# Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.
# Disable libata (CONFIG_ATA) entirely, and enable CONFIG_BLK_DEV_IDE_SATA.
# (newer choice, with less field testing) Disable CONFIG_IDE, and permit libata to run all your IDE and SATA ports.

The problem is that I don't know how to implement it. I mean I don't know which commands or steps I have to do.

Many thanks,

Julian

---

### Post by jpkotta on 2009-01-16
> # Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.

That one's easy.  Edit /boot/grub/menu.lst.  Add the option to the kernel lines and the defaults.  I'm posting examples, don't copy and paste them.

```
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dcfff082-0b76-45cc-9288-80383392a753 ro **combined_mode=libata**

```

```
title           Ubuntu 8.10, kernel 2.6.27-9-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.27-9-generic root=/dev/md1 ro quiet splash **combined_mode=libata**
initrd          /initrd.img-2.6.27-9-generic
quiet

```

The solutions require recompiling the kernel.  There are many threads on here that explain that.

---

### Post by JulianLx on 2009-01-17
Thanks jpkotta,

I hoped the solution was simpler than that. I think it will better to report a bug and waiting a couple of weeks more for a solution before doing an actualization to 8.10 or a clean install.

---

### Post by jpkotta on 2009-01-18
> **JulianLx said:**
> Thanks jpkotta,

I hoped the solution was simpler than that. I think it will better to report a bug and waiting a couple of weeks more for a solution before doing an actualization to 8.10 or a clean install.

What is simpler than that?  You just edit a text file.  In fact, you don't even need to edit the file, because you can manually edit the lines from Grub itself (but they won't be saved).  From the Grub countdown, press ESC to get to the menu.  Then follow the instructions for editing boot entries.

---

### Post by JulianLx on 2009-01-21
I tried with both options, libdata and ide. Neither worked.
I will not recompile the kernel. After two and a half years of using Ubuntu, I'm finding that after Vista release Ubuntu is going worse and worse. It cannot even manage my IDE disks that once worked smoothly.
If I have to play with configuration files and even to compile my kernel, I prefer Debian.

I quit.

Julian

---

