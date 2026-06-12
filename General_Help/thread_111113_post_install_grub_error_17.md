---
title: "post install: grub error 17"
date: 2006-01-01
forum: General Help
---

### Post by mendieta on 2006-01-01
Hi

I just installed Kubuntu in a separate partition, in hda5. Kubuntu's Grub is installed in hda5. My main distribution is installed in another disk, sda. 

My main distribution is installed in another disk, sda. 
Its lilo has the following entry:
```

other=/dev/hda5
        label="kubuntu"

```

So, when I get to the lilo prompt, I select kubuntu, and kubuntu's grub is loaded properly. However, after choosing the kernel to boot, I get the error:

```

Error 17 Cannot mount selected partition

```

According to grubs manual ([http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)), "This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. "

I wonder why. The filesystem is ext3. Shouldn't this be recognized by grub ???

Thanks in advance,
Mendieta

---

### Post by mendieta on 2006-01-01
Sorry, I forgot to show the main entry in the kubuntu grub menu.lst

```

title           Ubuntu, kernel 2.6.15-8-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-8-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-8-386
savedefault
boot

```

---

### Post by mendieta on 2006-01-01
Ok, I solved it. I am loading Ubuntu from the main lilo (the one for the main distro):

```

image=/root2/boot/vmlinuz-2.6.15-8-386
        label="kubuntu-direct"
        root=/dev/hda5
        initrd=/root2/boot/initrd.img-2.6.15-8-386
        append="noapic nolapic acpi=ht"

```

Of course, "/root2" is the mount point for /dev/hda5 in the main distro. 

Unfortunately, dhcp is not working properly in kubuntu and I cannot  get to the internet. In my other distro (and also in kubuntu live) dhcp works perfectly (it connects to my dsl cable modem just dandy). My idea was to setup kubuntu as a second distro, configure it to my liking and then switch. I guess I'll have to wait for  a new kubuntu release and see :-(

I really wish (k)ubuntu would allow you to install from the live-cd, since the live-cd autodetecs pretty much everything perfectly. Oh well ...

Cheers,
Mendieta

---

