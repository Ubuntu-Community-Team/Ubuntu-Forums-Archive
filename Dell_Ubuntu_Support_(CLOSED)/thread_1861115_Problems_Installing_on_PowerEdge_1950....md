---
title: "Problems Installing on PowerEdge 1950..."
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jxbadam on 2011-10-15
Hello All!

I am trying, rather unsuccessfully to get Ubuntu 11.04 desktop to install on a Dell Power Edge 1950.

The LiveCD will boot fine and allow me to both play around with and install Ubuntu. The problem occurs after the installation is completed. When I attempt to boot into the installation on the virtual disk I am presented with the rather unhappy "grub rescue>" prompt.

I have tried recovering the system from the "grub rescue>" prompt, but most activities are greeted with the (almost helpful) "error: out of disk." When I perform an 'ls' at the rescue prompt I am given a list with 4 entries something like
(HdX), (HdX, 1), (HdX, 2), (HdX, 3)
I am sorry, but I do not have that up on the console currently so I am merely giving a representation and not the actual output.

Additional information:
The machine has a Perc 6/i RAID controller. I have installed 4 SATA drives (750Gb) and have a 2.2Tb array configured RAID 5.

I had previously used 4 SAS drives (73 Gb) in a RAID 5 arrangement and was able to both successfully install and boot Ubuntu 11.04 desktop.

I am fairly sure that this isn't enough information to completely diagnose my problems, but hopefully a good start.

Any help that anyone can provide would be greatly appreciated.

-Adam

P.S. I am currently attempting a clean installation though I anticipate this will not work. I am doing this to get back to a 'clean' system, as I had booted the LiveCD previously and hacked around a little with grub.cfg.

---

### Post by jxbadam on 2011-10-15
Additional information:

I have reinstall Ubuntu 11.04 Desktop.

I am still dropped to the "grub rescue>" prompt with an error: out of disk. message.

This is what I tried (with no luck)
```

grub rescue> ls
(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
grub rescue> ls (hg0,gpt2)/
./ ../ lost+found/ <snip (rest of root file system)>
grub rescue> set
prefix=(hd0,gpt2)/boot/grub
root=hd0,gpt2
grub rescue> ls (hd0,gpt2)/boot
error: out of disk.

```

Also just to prove I wasn't crazy I swapped the SAS disks back in and then booted and Ubuntu came up just fine.....

---

### Post by SeijiSensei on 2011-10-15
It's likely that the PERC driver wasn't installed.  Can you see the array as a single device if you boot from the LiveCD but not after installation?

---

### Post by jxbadam on 2011-10-15
A good question...

When I boot via the LiveCD I see the array as a 2.2Tb drive in the 'Places' menu. If I mount the drive (it usually mounts to /media/UUID/) then I can browse into the installation.

When I try to boot directly from the array I get through all of the BIOS prompts (including the LSI prompt about the virtual drive being found/handled by BIOS) and then after the remote management boot up I am dropped to the "grub rescue>" prompt.

How can I tell if the driver is loaded?

Also it should be the '**amr** - MegaRAID SCSI/ATA/SATA RAID driver', correct?

---

### Post by jxbadam on 2011-10-15
I have found a bug report that seems to indicate this is a problem that was found, fixed, but is now ongoing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091)

The bug appears to be in the installer. Hopefully we can come up with a work around that isn't massively difficult.

---

### Post by jxbadam on 2011-10-15
So just to follow up with the bug report I downloaded Ubuntu 10.04.2 Desktop. Sadly this had the same problem. I am going to next try 11.10 since that was recently released.

If that fails I am not sure where to go on the Ubuntu front, perhaps I'll try some of the Ubuntu server installs.

---

### Post by jxbadam on 2011-10-15
Another failed attempt.

This time I added megaraid_sas to /etc/modules.

No dice.

---

### Post by SeijiSensei on 2011-10-17
> **jxbadam said:**
> When I try to boot directly from the array I get through all of the BIOS prompts (including the LSI prompt about the virtual drive being found/handled by BIOS) and then after the remote management boot up I am dropped to the "grub rescue>" prompt.

I've always avoided booting from an array.  I much prefer having a smaller drive that holds /boot and the OS and mounts the array as needed.  Because /var and /home can be mounted when the system goes multi-user, I'll put them on the array and leave the rest of the system on the boot drive.

---

### Post by jxbadam on 2011-10-17
A great idea, if only the machine had a drive outside of the array. Sadly the machine only holds 4 drives, if I take one drive out of the array to use as a boot disk then I'll lose the speed/redundancy that I gain from the array.

However I agree with your assessment. 

In this case I was unable to get Ubuntu to boot.

When I (eventually) build my next machine I'll make sure to have a dedicated boot drive (perhaps RAID 1).

Thank you for your help and suggestions :-)

---

### Post by SeijiSensei on 2011-10-17
I've thought about installing the OS to a bootable USB stick in situations like yours.  I've made bootable USB versions of the Ubuntu installation disks but haven't yet tried installing the OS to the USB stick in lieu of a hard drive.

---

