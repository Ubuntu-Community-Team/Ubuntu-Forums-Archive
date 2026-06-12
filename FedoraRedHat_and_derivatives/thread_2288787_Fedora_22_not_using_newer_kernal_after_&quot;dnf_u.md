---
title: "Fedora 22 not using newer kernal after &quot;dnf update&quot;"
date: 2015-07-29
forum: Fedora/RedHat and derivatives
---

### Post by Hodevah on 2015-07-29
Hello. I have had this problem for quite some time and have not been able to suffieciently resolve it. It's been ongoing since Fedora 21 as I recall. It is now prevelent in Fedora 22. 
Post update using dnf, a newer linux-image kernel may be installed; however, it normally should be taking over the older/previous kernel used. I am still using kernel 4.0.5 while the newest kernel version as can be seen below is 4.1.2.
Looking to have this resolved, please. 

I have Googled this problem using search terms such as '*fedora not using updated kernel'* but I don't receive too many results that are geared toward this problem. Is it just a simple matter of **dnf remove 4.0.5-300.fc22.x86_**and then update grub (by the way, grub is actually managed by another Linux OS, so therefore, I would need to update grub via the other Linux OS). 

 I would rather ask first before performing said action as I'm afraid that, that command will leave me without a kernel to boot Fedora 22. That is, not too familiar if kernel  **4.0.8** would automatically be subject to the new kernel to boot with post removal of **4.0.5**


Here are some outputs.

```
[frankenstein@localhost ~]$ uname -a
Linux localhost.localdomain 4.0.5-300.fc22.x86_64 #1 SMP Mon Jun 8 16:15:26 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```


```
[frankenstein@localhost ~]$ uname -r
4.0.5-300.fc22.x86_64
```


```
frankenstein@localhost ~$ rpm -q kernel
kernel-4.0.5-300.fc22.x86_64
kernel-4.0.8-300.fc22.x86_64
kernel-4.1.2-200.fc22.x86_64
```

Thank you in advance for your help in this interest of mine.

---

### Post by QDR06VV9 on 2015-07-30
Hi Hodevah.
So have you done this yet?
> [COLOR=#000000]grub is actually managed by another Linux OS, so therefore, I would need to update grub via the other Linux OS). [/COLOR]
I have to do that by The OS that is managing grub every time a new kernel gets installed, just to see it in the Advanced section of grub.
So in other words Fedora gets an updated or new kernel and i run the update grub command I will not see it until  I have updated grub from 
the OS in my case trusty that manages grub.
Hope that helps.
Kind Regards

---

### Post by Hodevah on 2015-07-30
Hi runrickus. Yes, I have done that many times. However, updating grub from Antergos will only update the grub menu that it is in control of. 

You see, if Fedora 22 has installed, but is not managed by the newer kernel, then it doesn't matter that I update Grub, managed by Antergos. It still won't be using the newer kernel. I need to somehow manipulate Fedora 22 to using the newer kernel. 
I just don't know how. And since yum has been deprecated and dnf is now the new package management system/structure for future Fedora releases, not all of the former yum commands have their equivalent in fedora. 

for example, "yum upgrade kernel XXXXX" doesn't translate for " dnf upgrade kernel XXXX"

Again, as listed earlier, here is what I have:

```
dnf list installed "kernel-"
negativo17 - Steam                                                                                                                                                      12 kB/s | 8.5 kB     00:00    
Last metadata expiration check performed 0:00:00 ago on Thu Jul 30 19:16:29 2015.
Installed Packages
kernel.x86_64                                                                                  4.0.5-300.fc22                                                                                   @System
kernel.x86_64                                                                                  4.0.8-300.fc22                                                                                   @System
kernel.x86_64                                                                                  4.1.2-200.fc22                                                                                   @System



```

I think it all matches:

```
 ls /boot/config-4.0.5-300.fc22.x86_64  extlinux                                                 initramfs-4.1.2-200.fc22.x86_64.img  System.map-4.1.2-200.fc22.x86_64
config-4.0.8-300.fc22.x86_64  grub2                                                    initrd-plymouth.img                  vmlinuz-0-rescue-59ee16a395aa4cfb928263ecdffa55fa
config-4.1.2-200.fc22.x86_64  initramfs-0-rescue-59ee16a395aa4cfb928263ecdffa55fa.img  memtest86+-5.01                      vmlinuz-4.0.5-300.fc22.x86_64
efi                           initramfs-4.0.5-300.fc22.x86_64.img                      System.map-4.0.5-300.fc22.x86_64     vmlinuz-4.0.8-300.fc22.x86_64
elf-memtest86+-5.01           initramfs-4.0.8-300.fc22.x86_64.img                      System.map-4.0.8-300.fc22.x86_64     vmlinuz-4.1.2-200.fc22.x86_64



```

should I use "[COLOR=#000000][FONT=liberation mono][B]initramfs"

[/B]&#8203;Thank you in advance for helping me resolve this problem if anyone can help me. [/FONT][/COLOR]

---

### Post by Hodevah on 2015-08-01
Hi. Is anyone still able to help me out in with this concern?
Thank you in advance.

---

### Post by buzzingrobot on 2015-10-10
This is old, I know, but this may be involved:  Fedora defaults to retaining the old kernel(s) and keeping at least one of them in the grub boot menu. I've caught it sometimes still using the previous kernel after a new one has been installed. (Seems to happen more with a development release.) When it does happen, the older kernel is clearly highlighted in grub's boot menu, so I just cursor to the new kernel.  If I'm industrious I fix it in the config file and rebuild grub.  I would imagine that if another distro's grub is in use, then its config file could be edited appropriately to use the right Fedora kernel.

BTW, dnf in F23 has picked up most, or all, or yum's functionality.

---

