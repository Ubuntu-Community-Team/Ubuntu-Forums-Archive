---
title: "Recent update killed MacBook Pro (2006) video/booting"
date: 2015-06-15
forum: Desktop Environments
---

### Post by joe172 on 2015-06-15
Hello all,

After a recent update my 14.04.1 version of Xubuntu no longer boots all the way. To install the software originally I had to edit the grub file and add the "nomodeset" option as well as uninstall nvidia drivers. It seems the recent update reversed these changes.

I've since gone in via recovery mode and removed all Nvidia drivers and tried changing several grub options:

The end of the "linux" line in grub looks like the following. When I boot with this it freezes at a line about loading the ramdisk and then the video goes black:
```

quiet splash $vt_handoff

```

When I change it to the following it pauses at "Loading initial ramdisk..."
```

nomodeset $vt_handoff

```

When I change it to the following it shows the xubuntu splash screen, the circle spins and then it freezes.
```

quiet splash $vt_handoff nomodeset

```

When I change it to the following it shows the xubuntu splash screen, the circle spins and then it freezes (same as above).
```

quiet splash nomodeset

```

When I change it to the following it starts to boot but then freezes at "Stopping System V runlevel compatibility".
```

nomodeset

```

Any suggestions on how to resolve this?

Thanks!

---

### Post by joe172 on 2015-06-18
Any suggestions? Thanks

---

