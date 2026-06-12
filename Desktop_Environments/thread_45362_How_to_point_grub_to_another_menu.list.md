---
title: "How to point grub to another menu.list?"
date: 2005-06-29
forum: Desktop Environments
---

### Post by foxy123 on 2005-06-29
I have installed a second version of Ubuntu to a second HD. So now grub uses menu.list from it. How can I point it back to my old installation?

---

### Post by dickohead on 2005-06-29
[QUOTE=foxy123]I have installed a second version of Ubuntu to a second HD. So now grub uses menu.list from it. How can I point it back to my old installation?[/QUOTE]
 you might find that GRUB isn't using menu.lst from your second, rather it is using the boot partition, aswell as the possibility of MBR records written in by your second install. I overcame the issue of booting two distros by creating a boot partition on the first harddrive and storing all my info there. So then the machine will prompt you with your primary GRUB menu, and then you just need to add the entries for your second hard drive to your primary menu.lst file... hope that helps!

---

### Post by irusun on 2005-06-29
If you want to keep both installations, just edit the menu.lst and add the original location to the list.  But if you want to bomb the second installation, that's not going to work very well - so...

To install grub so it permanently points to a different partition, it's best to use a grub boot disk/cd (or some livecd with grub installed). After booting the grub disk, at the command line, you can do the following:

First, find the partition that actually holds grub files (grub's root device).  In your case, it may find a couple - one the first hard drive and the second hard drive.  Note the partition of the one you want grub to point to.

grub> find /boot/grub/stage1
or
grub> find /grub/stage1

Next, set the GRUB's root device to the boot directory of Ubuntu. GRUB’s root device is the partition that the GRUB files are located on as noted above.

For example, if the GRUB files are located on your first logical partition, then:

Example:
grub> root (hd0,4)

Once you've set the root device correctly, run the command "setup". 

To install grub to the MBR of the first hard drive, then:

Example:
grub> setup (hd0)

That should hopefully do it.

---

### Post by foxy123 on 2005-06-30
[QUOTE=irusun]If you want to keep both installations, just edit the menu.lst and add the original location to the list.  But if you want to bomb the second installation, that's not going to work very well - so...

To install grub so it permanently points to a different partition, it's best to use a grub boot disk/cd (or some livecd with grub installed). After booting the grub disk, at the command line, you can do the following:

First, find the partition that actually holds grub files (grub's root device).  In your case, it may find a couple - one the first hard drive and the second hard drive.  Note the partition of the one you want grub to point to.

grub> find /boot/grub/stage1
or
grub> find /grub/stage1

Next, set the GRUB's root device to the boot directory of Ubuntu. GRUB’s root device is the partition that the GRUB files are located on as noted above.

For example, if the GRUB files are located on your first logical partition, then:

Example:
grub> root (hd0,4)

Once you've set the root device correctly, run the command "setup". 

To install grub to the MBR of the first hard drive, then:

Example:
grub> setup (hd0)

That should hopefully do it.[/QUOTE]

do you know if I can do it with Ubuntu Live CD. I also have knoppix and System Rescue Linux 0.2.15.

---

### Post by irusun on 2005-06-30
[QUOTE=foxy123]do you know if I can do it with Ubuntu Live CD. I also have knoppix and System Rescue Linux 0.2.15.[/QUOTE]
I believe so - at the command line type:
grub

To quit grub, type:
quit

---

### Post by mingus on 2005-06-30
umm . . . doesn't using the live-CD require mounting the drive and chrooting to the mount point?

---

### Post by duffmckagan on 2005-06-30
I recently found a new method to do that.

Add this to your existing /boot/grub/menu.lst(New Ubuntu installation.)

```


Title Ubuntu Previously Installed
 rootnoverify (hd0,2)
 chainloader +1

```

Make sure to put the correct path in the 

rootnoverify section.

If you first ubuntu installation is placed on suppose hda2, use this.

rootnoverify (hd0,1)

I hope this will work.

Post back with the results.

---

### Post by irusun on 2005-06-30
[QUOTE=mingus]umm . . . doesn't using the live-CD require mounting the drive and chrooting to the mount point?[/QUOTE]
I stand corrected on the Ubuntu Live-CD (I have never used it myself - but I thought I read there was a "rescue" command at first boot - maybe this is only on the "Ubuntu Install CD"?).

The mentioned "System Rescue" cd should work for this purpose (according to their web site).  Personally, I use a dedicated Grub boot cd.

---

### Post by irusun on 2005-06-30
[QUOTE=duffmckagan]I recently found a new method to do that.[/QUOTE]
To do what?

What you describe is if Foxy123 wants to keep both installations (i.e. chainload from the second installation to the first)?

EDIT: It's a little confusing to know which way to go since Foxy123 never clarified: keep both installations with choice to boot to either one - or use only one so the other can be deleted...

---

### Post by duffmckagan on 2005-06-30
I think that he wants to keep both the installations and is struggling to do that.

I think that chainloading the previous installation from the first one, should do the job.

---

### Post by irusun on 2005-07-01
[QUOTE=duffmckagan]I think that chainloading the previous installation from the first one, should do the job.[/QUOTE]
Sounds good.

May want the "makeactive" in there - but I'm not sure...
Example:
```
title		Other Grub Menu List
root		(hd0,1)
makeactive
chainloader	+1
```

If Foxy123 wants to skip loading grub twice every time to access the other installation, put a menu entry in grub pointing directly to the other kernel.
Example:
```
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
```

---

### Post by mingus on 2005-07-01
*I thought I read there was a "rescue" command at first boot - maybe this is only on the "Ubuntu Install CD"?*

Yes, rescue is on the install CD, and drops you into a chroot'ed mount.  The live-CD creates a RAM image (like Knoppix), nothing is mounted.  Also, grub isn't on it.

*I think that chainloading the previous installation from the first one, should do the job.*

Both methods work fine.  It can be done by an explicit call to the kernel (the way Debian's update-grub script builds menu.lst) or chain-loading (the way SuSE does it).  The former integrates boot into a single loader and menu file.  With the latter, grub needs to be installed in a second location, and the boot process is two-steps.

FWIW, I've found that the former works well with multiple copies of the same distro (I have 2 SuSE's and 3 Ubuntu's) while the latter is better with distinctly separate distros (I chain-load between Yoper, Gentoo, Xandros, and Vector).  Purely a matter of pref.

---

### Post by mingus on 2005-07-01
*May want the "makeactive" in there - but I'm not sure...*

*rootnoverify (hd0,1)*

Both these commands are primarily for unsupported OS's, principally Windows.  Rootnoverify tells grub not to mount the filesystem, and makeactive sets the partition (it must be a primary) as active which is a requirement for Windows to boot.

Chainloader was also created primarily for this purpose, although it works great with supported OS's as well.

---

### Post by irusun on 2005-07-01
Thanks for clearing that up!

---

### Post by foxy123 on 2005-07-01
[QUOTE=duffmckagan]I think that he wants to keep both the installations and is struggling to do that.

I think that chainloading the previous installation from the first one, should do the job.[/QUOTE]

Sorry for some confusion. No I do not want to keep my second installation. I made it only for the purpose to restore the users on the old one. So I want to ditch the second and keep the first. That's why I have to make sure that grub uses a proper menu.lst.

Thanks a lot for the advice guys, I will try to do it tonight....

---

### Post by mingus on 2005-07-01
Gosh guys, we sure did overkill . . .

---

### Post by foxy123 on 2005-07-02
Thank you guys, everything is fine now!

---

### Post by duffmckagan on 2005-07-02
[QUOTE=foxy123]Thank you guys, everything is fine now![/QUOTE]
 Ubuntu Rocks.

Cheers.

---

