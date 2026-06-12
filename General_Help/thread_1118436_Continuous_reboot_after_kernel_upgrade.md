---
title: "Continuous reboot after kernel upgrade"
date: 2009-04-07
forum: General Help
---

### Post by minus24 on 2009-04-07
I'm running Xubuntu 8.10.  I just upgraded to kernel 2.6.27.11, using the Package Manager, as usual.  A system restart was required, so I clicked the icon, and now Xubuntu keeps rebooting.  I get the BIOS loading screen, then my choice of OSes: Xubuntu 8.10, Arch, and openSUSE 11.0.  If I choose Arch, the system boots fine.  (I use chainloader directives to boot into the three choices.)  However, if I choose Xubuntu, almost immediately I get the BIOS loading screen again.

Any ideas on what could cause this?  Do I perhaps need to reload GRUB in my Xubuntu partition?

---

### Post by bcschmerker on 2009-04-07
> **minus24 said:**
> I'm running Xubuntu 8.10.  I just upgraded to kernel 2.6.27.11, using the Package Manager, as usual...and now Xubuntu keeps rebooting.  I get the BIOS loading screen, then my choice of OSes: Xubuntu 8.10, Arch, and openSUSE 11.0.  If I choose Arch, the system boots fine.  (I use chainloader directives to boot into the three choices.)  However, if I choose Xubuntu, almost immediately I get the BIOS loading screen again.

Any ideas on what could cause this?  Do I perhaps need to reload GRUB in my Xubuntu partition?It looks as though something got corrupted either in the xubuntu partition or in the chainloader.  I ran into a similar situation when I upgraded my hardware and had to reinstall Ubuntu 7.10; as it turned out, I needed a true SATA optical drive along with my Everex' new Elitegroup GeForce6100SM-M V1.0, as the EIDE-to-SATA converter piggybacked to my stock ATAPI DVD transport couldn't do the job on a live boot.  Your problem has a different origin.

You're right about one possibility, namely a bad configuration file for GRUB.  The second possibility that comes to mind is a bad initrd.img, which would result in a disc boot failure; the third is a bad configuration for the chainloader.  Does it boot OK in both arch and openSuSE, narrowing the problem to the initrd.img in xubuntu?

---

### Post by minus24 on 2009-04-07
Thanks for your suggestions.  Yes, it boots OK into both Arch and openSUSE.  When I select Xubuntu it reboots almost immediately (without the 3 second delay I've specified in the Xubuntu menu.lst), so I don't think it's had chance to even look at the initrd.img.  Does that sound reasonable?  I will try reloading GRUB to the Xubuntu partition in the morning.

Thanks again.

---

### Post by minus24 on 2009-04-07
I resolved this problem by booting into Arch and reloading GRUB.  I actually screwed up at first by installing GRUB not into the Xubuntu partition (as I intended) but into the MBR, thus:

```
mount /xubuntu
grub-install --root-directory=/xubuntu /dev/sda
```

I believe the grub-install should have been into /dev/sda10 (the Xubuntu partition.)  Anyway, when I rebooted I did not get the usual choice of OS options; instead I went straight into Xubuntu!  Yay - partial success!

In Xubuntu, I then reinstalled the initial GRUB menu (which chainloads to Xubuntu, Arch, and openSUSE) to the MBR:

```

grub
install (hd0,5)/boot/stage1 d (hd0) (hd0,5)/boot/stage2 (hd0,5)/boot/menu.lst
quit
```

Finally, I installed GRUB to the Xubuntu (now root) partition:

```
grub-install /dev/sda10
```

And now all is well.  Phew!

This is the second time something like this has happened to me with Ubuntu.  The first time around, with Gutsy Gibbon, Ubuntu would hang at stage 1.5 or stage 2 (I forget which.)  Different symptom, but reinstalling GRUB into the Gutsy partition fixed the problem.

---

