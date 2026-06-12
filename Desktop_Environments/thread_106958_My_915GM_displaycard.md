---
title: "My 915GM displaycard"
date: 2005-12-21
forum: Desktop Environments
---

### Post by yubigfish on 2005-12-21
Can Ubuntu makes 915GM work itself?Or need I download driver from Intel to makes this displaycard work?

My laptop is IBM R52



Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

(Copy from xorg.conf)

---

### Post by kairu0 on 2005-12-21
My 915GM card (in my Sony Vaio VGN-FS21 laptop) worked almost perfectly out of the box.

At first, I got bad 3d performance, but that changed when I added the "drm" module to xorg.conf.

---

### Post by yubigfish on 2005-12-25
[QUOTE=kairu0]My 915GM card (in my Sony Vaio VGN-FS21 laptop) worked almost perfectly out of the box.

At first, I got bad 3d performance, but that changed when I added the "drm" module to xorg.conf.[/QUOTE]



could you show me your "drm"module to me?so I can copy it into myxorg.conf.
Thank you!

---

### Post by kairu0 on 2006-01-05
All you do is add:

```
Load        "drm"
```

to the module section (it's marked by "Section 'Module'") of /etc/X11/xorg.conf.

---

