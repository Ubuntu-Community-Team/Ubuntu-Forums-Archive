---
title: "Kernel Panic"
date: 2005-06-09
forum: Desktop Environments
---

### Post by bhound89 on 2005-06-09
I recently got the new kernel update from synaptic, and I just rebooted, and it gives me the error
Kernel Panic: not syncing: VFS: Unable to mount root fs on unknown block (0,0)

I tried the recovery mode, and got the same result.

I am using GRUB boot loader, if that helps in any way.

---

### Post by defkewl on 2005-06-09
Try posting your /etc/fstab and /boot/grub/menu.lst

Btw, try searching the forums, there has been many issues related to this.

---

### Post by zAo on 2005-06-09
[QUOTE=defkewl]Try posting your /etc/fstab and /boot/grub/menu.lst

Btw, try searching the forums, there has been many issues related to this.[/QUOTE]
What type of Filesystem do you use for / ? Reiser?

---

### Post by darge0flex on 2005-06-09
Same problem here using reiserfs for root and ext2 for boot...

```

.
.
.
Uncompressing Linux... Ok, booting the kernel.
audit(1118306259.993:0): initialized
Please append a correct "root=" boot option
Kernel panix - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

---

### Post by darge0flex on 2005-06-09
my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs defaults        0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto,exec  0       0

```

and my menu.lst:
```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.10-5-686
root            (hd0,0)
kernel          /vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd          /initrd.img-2.6.10-5-686
savedefault 
boot

title           Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd          /initrd.img-2.6.10-5-686
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /memtest86+.bin  
savedefault
boot    

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by zAo on 2005-06-09
The kernel you are trying to boot, has ReiserFS as module I think. It needs to be compiled in the kernel to mount the rootfs.
Try to build a custom kernel or use your old kernel.

---

### Post by darge0flex on 2005-06-09
Woundering that it worked flawlessly before the last kernel-security-update comes into place...

---

### Post by darge0flex on 2005-06-09
I've this problem several times with gentoo and grub. Try switching to lilo, in the past it helps...

---

### Post by bhound89 on 2005-06-09
I would post those things, but I don't know how to get into my system. (I'm on windows now)

---

### Post by braunsfeld on 2005-06-10
[QUOTE=zAo]The kernel you are trying to boot, has ReiserFS as module I think. It needs to be compiled in the kernel to mount the rootfs.
Try to build a custom kernel or use your old kernel.[/QUOTE]

I have the same problem with Reiserfs. I was suprised that the update-script doesn't move the old kernel to vmlinuz.old. Now I am running a Kernel from a Live-CD copied to my hard-disc. 

Imho this is a bug. The reiserfs-module should be compiled in the first place and not by the user...

---

### Post by braunsfeld on 2005-06-10
My bad. I had libc6 from breezy installed which caused the problem:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11135](https://bugzilla.ubuntu.com/show_bug.cgi?id=11135)

This helped me as in [https://bugzilla.ubuntu.com/show_bug.cgi?id=11135#c4:](https://bugzilla.ubuntu.com/show_bug.cgi?id=11135#c4:)

- wget breezy package of initrd-tools
- dpkg -i initrd-tools
- dpkg-reconfigure installed linux-image packages
- then reboot.

---

### Post by bhound89 on 2005-06-10
can someone please tell me what to do?

---

