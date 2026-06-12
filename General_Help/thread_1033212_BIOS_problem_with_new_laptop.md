---
title: "BIOS problem with new laptop"
date: 2009-01-07
forum: General Help
---

### Post by Ozor Mox on 2009-01-07
I have just bought a new laptop with no OS pre-installed which uses PhoenixBIOS. At first, the Ubuntu live CD would not boot at all, until I went into the BIOS and changed the 'installed operating system' option from 'Vista' to 'Other'. Now it boots, but I get the message from the kernel immediately before the splash screen:

"ACPI: DMI BIOS year==0, assuming ACPI-capable machine"

After Googling, it seems this is often a problem with either very old (which I can rule out!) or buggy BIOS software. Do I have to flash the BIOS and upgrade it? It seems like a risky process from what I have read.

---

### Post by anagor on 2009-01-07
I've flashed the bios numerous times on quite a few machines, without any issues, so it's not that risky.
However if you don't feel comfortable doing it, or there isn't any new version of your bios yet, and apart from this message, everything else is working fine, you don't have to flash it.

---

### Post by zipperback on 2009-01-07
What kind of laptop are you working with?

Is this error preventing Ubuntu from running on your laptop?

- zipperback

---

### Post by Ozor Mox on 2009-01-07
> I've flashed the bios numerous times on quite a few machines, without any issues, so it's not that risky.
However if you don't feel comfortable doing it, or there isn't any new version of your bios yet, and apart from this message, everything else is working fine, you don't have to flash it.

You're right, it's just I figured it would be something that needs fixing, since none of my other computers (up to 8 years old!) have this problem, and I've never done a BIOS upgrade on those. Since this is a brand new laptop, I wasn't really expecting a BIOS problem :(

> What kind of laptop are you working with?

A [Novatech X15 GS Pro](http://www.novatech.co.uk/novatech/range.html?t=nb&c=all&r=X15).

> Is this error preventing Ubuntu from running on your laptop?

Now that I have modified the BIOS settings, no. Though, I haven't yet installed it because I want to see what the company say about a stuck/dead pixel first. Also, I'm not sure if this is preventing or limiting the use of ACPI features.

---

### Post by RichardG891 on 2009-01-07
I've got an HP G6000 laptop with a Phoenix BIOS... Nil power management options. Same problem historically with Ubuntu 8.10. Try holding a key down throughout the boot process, or better boot on battery power and when the progress bar freezes, plug it into the mains.... If this works then its the same problem as mine... add this to the end of the default (top) boot script in grub's menu.lst:

hpet=disable

i.e.:

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		be7453f3-5b30-4cba-ab28-3f41b0f11aae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=be7453f3-5b30-4cba-ab28-3f41b0f11aae ro hpet=disable quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

---

### Post by Ozor Mox on 2009-01-14
Little update. I messed about with a ton of boot options to see what difference it made. acpi=force, noapic, nolapic, hpet=disable and acpi_irq_balance all did nothing. acpi=off stopped the OS from booting at all (although the message didn't appear :))

I think I've definitely tracked down the source of the problem. I ran dmidecode and found this nice little rogue line in the output:

```
Release Date: 10/02/0892
```

How messed up is that?! I'm guessing my BIOS would need flashing to correct a blunder like that. I'm going to take the laptop back to the shop and see what they say about it thinking the BIOS software was released before the invention of electricity :D

---

