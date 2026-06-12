---
title: "Recovery mode text size and possible Vesa probs"
date: 2009-01-03
forum: General Help
---

### Post by hpp3 on 2009-01-03
When I boot into Recovery Mode, my text display is huge, as in the characters are really large and text mode is almost unusable.
I have tried all the 'vga=791' tricks in /boot/grub/menu.lst to no avail. Either I get no screen at all or a 40x25 one. 
Dmesg has some interesting reports around line 220, could this be the source of the problem?:
```
...
[    3.821915] uvesafb: failed to execute /sbin/v86d
[    3.821989] uvesafb: make sure that the v86d helper is installed and executable
[    3.822126] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    3.822194] uvesafb: vbe_init() failed with -22
[    3.822267] uvesafb: probe of uvesafb.0 failed with error -22
...
```
I have the v86d package installed (it was not previously, and I got this same error, so installed and rebooted... still there)

Running 'modprobe nvidiafb' while in Recovery Mode gives me a nice screen, but how do I get there from GrUB?

BTW- 
-This did not happen with Xubuntu 8.04.
-My video card is a RivaTNT2 (yes, quite old I'd say) and the 'nv' driver won't load in X also. Whether I use a custom xorg.conf or the default one with 'nv' instead of 'vesa'. X runs fine, but the only driver that shows up in 'lsmod' is fbcon. 'modprobe nv' gives 'FATAL: Module nv not found" error. 
This stuff also did not happen in 8.04

---

