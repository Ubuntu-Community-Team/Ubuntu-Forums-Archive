---
title: "synaptic Mark All Upgrades &gt; GRUB error 11"
date: 2009-06-25
forum: General Help
---

### Post by FPtje on 2009-06-25
Hi, I have installed linux based on ubuntu and I really liked it...

Until I broke it with synaptic...

Basically I opened synaptic, clicked the "Mark All Upgrades" button, Clicked apply, shut down all applications and reboot.

Whenever I try to boot linux mint now in GRUB(either linux mint gloria 7 or the recovery)
it instantly says:
Error 11: Unrecognized device string


When I select the linux mint Gloria and press E(edit) I see this:
```

root d0530466-d6de-453a-8301-8dd2ee6d1f2b
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=d0530466-d6de-453a66-d6de-453a-8031-8dd2ee6d1f2b ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

```
(please don't blame me for a mistake)

Note: One of the packages was linux-generic... Wasn't that the linux kernel?

Please help! I'm a linux noobie

---

### Post by prshah on 2009-06-25
> **FPtje said:**
> 
```

[color="red"]title [/color] d0530466-d6de-453a-8301-8dd2ee6d1f2b
kernel /boot/vmlinuz-2.6.28-13-generic root=[color=red]UU10[/color]=d0530466-d6de-453a66-d6de-453a-8031-8dd2ee6d1f2b ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

```


Add the word "title" before the UUID in the first line; you can also just comment it out with a "#" and add your own title to it.

And, in the second line, it's UUID (you-you-eye-dee), not UU10.

You should then be able to boot; make the changes permanent by editing your /boot/grub/menu.lst file.

---

### Post by FPtje on 2009-06-25
UU10 and UUID was a type mistake, I'm sorry

I will try that title thing now, thanks a lot

Edit:
Apparently it said this:
```
_root_ d0530466-d6de-453a-8301-8dd2ee6d1f2b
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=d0530466-d6de-453a66-d6de-453a-8031-8dd2ee6d1f2b ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet
```

Changing "root" to "title" gives error:
Error 27: Unrecognized command

---

### Post by prshah on 2009-06-25
> **FPtje said:**
> UU10 and UUID was a type mistake, I'm sorry
Changing "root" to "title" gives error:
Error 27: Unrecognized command

No you shouldn't change "root" to "title".

root should be (ex) (hd0,1) or so, depending on your setup. Eg```
root    (hd0,1)
```

Can you check against other entries in the /boot/grub/menu.lst file?

Alternately, boot off a live CD, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo fdisk -l
``` and post back the output here for the correct "root" parameters.

---

### Post by FPtje on 2009-06-25
```
~ $ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93dcb1a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567       19933   147525497    7  HPFS/NTFS
/dev/sda3           19934       30401    84084210    5  Extended
/dev/sda5           19934       29969    80614138+  83  Linux
/dev/sda6           29970       30401     3470008+  82  Linux swap / Solaris

```

This is the result of sudo fdisk -l
On a live CD

---

### Post by prshah on 2009-06-25
> **FPtje said:**
> ```
~ $ sudo fdisk -l
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda5           19934       29969    80614138+  83  Linux

```


OK, I'd say your root is (hd0,5), but what is the "unknown" part? Yikes!?

Try booting again, at grub, press "e" to edit the line, replace the "root" line with ```
root (hd0,5)
```, then press enter, and "b" to boot.

If hd0,5 doesn't work, try (hd0,4).

---

### Post by FPtje on 2009-06-25
root (hd0,5)
>Error 17: Cannot boot from the selected partition

root (hd0,4)
Starting up...

:D

In other words it's working again!
YAAAAY!
HURRAAAAAAY!
Thanks a LOT man!
Dude! You're awesome!
Thanks!!!

But
I wonder how the bootloader broke in the first place, I didn't change it?
Anyway editing the menu.lst now to make the changes permanent!

---

