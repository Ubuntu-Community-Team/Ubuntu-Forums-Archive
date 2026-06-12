---
title: "Cups error about stdin and temporary file?"
date: 2009-02-19
forum: General Help
---

### Post by jamaas on 2009-02-19
I'm trying to print to a hp 2610 photosmart printer, it seems to install ok but when I print a page, CUPS gives this error message.

Can't copy stdin to temporary file"

I'm running Ibex of an eeepc 901 with so memmory and disk space is limited, is this the problem or is there another fix?

Thanks

Jim

---

### Post by dcstar on 2009-02-19
> **jamaas said:**
> I'm trying to print to a hp 2610 photosmart printer, it seems to install ok but when I print a page, CUPS gives this error message.

Can't copy stdin to temporary file"

I'm running Ibex of an eeepc 901 with so memmory and disk space is limited, is this the problem or is there another fix?

Thanks

Jim

Do you have sufficient free space in the /tmp filesystem?

I suspect that the eee setup puts this in RAM (to reduce writes to the solid-state disk) so it is a small size, and it may be too small for the temp file the print job creates.

---

### Post by jamaas on 2009-02-20
Thanks dcstar,

I thought it might be something like this with the limited disk/ram space.  Would anyone know how to diagnose if this is in fact the problem and how to fix it?  

Thanks

Jim

---

### Post by stonux on 2010-09-27
how to diagnose:

Enther the commmand [FONT="Courier New"]df[/FONT]

It will list the free space on all your disks. The output will look like:

```

$ df
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sda1               730120     47878    643286   7% /boot
/dev/sda3               758284    758140       144 100% /tmp
```

If the [FONT="Courier New"]%used[/FONT] column shows 100%, your /tmp filesystem is full.
Try to delete some unnecessary files.

In [FONT="Courier New"]/etc/fstab[/FONT], you have a list of filesystems to be mounted.
Check the size argument of tmpfs.

---

