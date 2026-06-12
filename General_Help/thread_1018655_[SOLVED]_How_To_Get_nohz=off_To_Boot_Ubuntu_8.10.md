---
title: "[SOLVED] How To Get nohz=off To Boot Ubuntu 8.10"
date: 2008-12-22
forum: General Help
---

### Post by vames on 2008-12-22
I'm having some problems here guys. Last time I had Ubuntu 8.10 on my acer aspire 5050 I could boot in just fine by nohz=off, I even found a work around that allows me not to type in nohz=off in every reboot. Anyway, I reinstalled and for some reason it's not working, sure i could boot by typing "noapic nolapic acpi=off" but that doesn't fix my video problems which runs very slow, it doesn't fix my acpi problems either.

I just want to know what I'm doing wrong, or if i need to download something for it to work. Help please, thanks

---

### Post by redilyn on 2008-12-22
You say you had to type this in after reboot?

Are you using this option with a grub boot entry or do you type if after you login??

I'm guessing grub option since you say you use noapic nolapic acpi=off to get in

Try this

If you using it as a grub option you can add it to your menu.lst

```

sudo gedit /boot/grub/menu.lst

```

Look for this section in the file
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```

and change it to
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
[COLOR="Red"]# defoptions=quiet splash nohz=off[/COLOR]

```

The

```

sudo update-grub

```

---

### Post by vames on 2008-12-22
It worked perfectly, thanks man

---

