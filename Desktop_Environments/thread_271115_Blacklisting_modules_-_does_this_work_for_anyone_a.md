---
title: "Blacklisting modules - does this work for anyone at all?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by kelt65 on 2006-10-04
No matter what I can't seem to preven the fb modules from loading, no matter what is in /etc/modprobe.d/blacklist-framebuffer.

This seems to work for some modules but not others.

I do not want the dozen or so frambuffer related drivers loading at boot or at any other time.

Short of removing them and recreating the ramdisk, how is this supposed to work?

lsmod | grep fb shows me:

vga16fb                14344  1
vgastate               10304  1 vga16fb
fbcon                  44640  73
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon

ALL of these modules are in /etc/modprobe.d/blacklist-framebuffer.

Can anyone tell me why they are loading? Am I missing something else?

Why doesn't the blacklist work at all?

I can only assume this happens when the kernel first boots and loads modules from the initrd.  What kernel parameters do I need to pass to prevent fb* modules from loading?  I removed "splash" and all the graphic stuff but no luck.

---

