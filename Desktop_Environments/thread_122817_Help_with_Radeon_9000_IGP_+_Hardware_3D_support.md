---
title: "Help with Radeon 9000 IGP + Hardware 3D support"
date: 2006-01-28
forum: Desktop Environments
---

### Post by s'neil on 2006-01-28
Got one of these in my laptop, and would like to get hardware 3d support so I can play WoW over wine!

I've tried the ATI drivers off the site and had a look at the DRI project, but none seem to work!

here is my fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

and my lspci
```

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 583                           5

```

and some lsmod action
```

fglrx                 439168  7
agpgart                34792  2 fglrx,ati_agp

```

When i try and run the DRI installer for the R200 chipsets i get the following...
```

Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        Copying extra files...done

Updating configuration:
        Removing old kernel module "radeon"...done
        Inserting new kernel module "radeon"...ERROR

```

and the log shows
```

WARNING: Error inserting drm (/lib/modules/2.6.12-10-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.12-10-686/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

so, any ideas? :)

---

