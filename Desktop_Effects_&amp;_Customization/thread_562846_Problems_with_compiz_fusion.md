---
title: "Problems with compiz fusion"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by Cubedude04 on 2007-09-29
Hey i installed compiz fusion a few months ago. everything worked fine then i upgraded my drivers to the restircted ones. and didn't use it for a month or so. I want to show some people how it looks so i disabled the restricted drivers and restarted my computer and typed

compiz --replace -c emerald &
emerald --replace &

the screen goes weird for a few seconds and the following things happen

The title bar on every program i launch vanishes

None of my effects like the cube or anything work

My cpu goes to max

My emerald theme doesn't change from the regular theme i have (ubuntu studio theme) which is GTK i believe

How can i fix these problems

Thanks in advance

---

### Post by b0rt on 2007-09-29
I have a very similar problem, but i just have installed compiz, the thing is that when i put ```
compiz --replace
```
all this errores comes out :
```
bort@Garoth:~$ compiz --replace
inotify_add_watch: No such file or directory
/usr/bin/compiz.real: pixmap 0x340018d can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x3202e03 to texture
/usr/bin/compiz.real: pixmap 0x340018d can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x3202e03 to texture
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks

/usr/bin/compiz.real: pixmap 0x340018d can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x3202e03 to texture
/usr/bin/compiz.real: pixmap 0x340018d can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x3202e03 to texture
/usr/bin/compiz.real: pixmap 0x340018d can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x3202e03 to texture
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: pixmap 0x340018d can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0x3202e03 to textur
```

---

### Post by Rupertronco on 2007-09-29
> **Cubedude04 said:**
> Hey i installed compiz fusion a few months ago. everything worked fine then i upgraded my drivers to the restircted ones. and didn't use it for a month or so. I want to show some people how it looks so i disabled the restricted drivers and restarted my computer and typed

compiz --replace -c emerald &
emerald --replace &

the screen goes weird for a few seconds and the following things happen

The title bar on every program i launch vanishes

None of my effects like the cube or anything work

My cpu goes to max

My emerald theme doesn't change from the regular theme i have (ubuntu studio theme) which is GTK i believe

How can i fix these problems

Thanks in advance

You need the restricted drivers ENABLED to run compiz. Also you don't need to type emerald --replace if your first command defines emerald as the window decorator (which yours does). So either run the compiz --replace -c emerald or run compiz --replace and emerald --replace as two separate commands.

---

### Post by Cubedude04 on 2007-09-29
When i had it working a few months ago i defiently didn't have restricted drivers on because i remember having to enable them to get a problem in blender to fix and compiz fusion didn't work after that 

anyway i restricted drivers just to test it anyway and it didn't work

james@Prothex-Desktop:~$ compiz --replace -c emerald &
[1] 5944
james@Prothex-Desktop:~$ Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Any other ideas?

---

