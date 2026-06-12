---
title: "Compiz won't replace emerald! :("
date: 2009-05-21
forum: General Help
---

### Post by gymophett on 2009-05-21
I have a great compiz theme I need to go with the rest of my desktop, but when I try to switch from Emerald back to compiz, I get this!

```
gavin@gavin-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:9613 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

Help. :)
Thanks.

---

### Post by mcduck on 2009-05-21
You can't replace Compiz with Emerald, or Emerald with Compiz. :)

Emerald is basically just a Compiz plugin. You can't run Emerald without running Compiz.

Unlike other window managers, Compiz doesn't handle drawing of the window borders by itseld, it assigns this tasks to extra program it calls "window decorators". Emerald is one of these window decorators, other alternatives are gtk-window-decorator (which uses Metacity themes that are also used by Gnome's default window manager) and kde-window-decorator (which uses Kwin themes).

If you want to make Compiz use Metacity themes (like it does on out-of-the-box Ubuntu install), the command you need is "gtk-window-decorator --replace", although you really should just configure which decorator youw ant to use in Compiz settings.

---

### Post by gymophett on 2009-05-21
I just ended up uninstalling Emerald as I didn't need it. Thanks for your help though man!

---

