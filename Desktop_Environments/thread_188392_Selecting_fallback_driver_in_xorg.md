---
title: "Selecting fallback driver in xorg ?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by mendieta on 2006-06-04
Dear All

I have an NVIDIA driver, and I would like to be able to do the following. When X starts, it will:
[LIST=1]
[*]Try to start nvidia proprietary driver
[*]If it fails, load the default (xorg) nvidia driver.
[/LIST]
This would be very useful for situations when nvidia does not load (like it happens sometimes after a kernel upgrade, or when loading an older kernel, etc.) Here is the relevant section of /etc/X11/xorg.conf:

```

Section "Device"
    Identifier     "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
    Driver         "nvidia"
    Option         "NvAGP" "3"
   # Driver         "nv"
EndSection

```

Note that the "nv" driver is commented out. I can edit the file by hand when it fails, but this is not a good solution. There should be a way of selecting a **SecondaryDriver** field (or similar). Or more in general, a list of drivers, to be tried one after the other. Is this possible at all ?

Thanks a lot in advance. Cheers !

---

### Post by mendieta on 2006-06-04
Let me add that the closest thing I found is this:
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/27020](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/27020)

But it not quite the same as I need. It is a universal fallback mechanism for the installer to a very, very basic graphics driver. What I am looking for is a customizable way of reporting a list of drives you want to try, in a certain order.

Anyway, I hope someone can help. I'll be glad to write a Tips and Tricks if we find a solution ...

---

### Post by matrooswolf on 2006-06-04
[QUOTE=mendieta]
I have an NVIDIA driver, and I would like to be able to do the following. When X starts, it will:
[LIST=1]
[*]Try to start nvidia proprietary driver
[*]If it fails, load the default (xorg) nvidia driver.
[/LIST]
This would be very useful for situations when nvidia does not load (like it happens sometimes after a kernel upgrade, or when loading an older kernel, etc.) [/QUOTE]

Very good suggestion!  =D>

---

