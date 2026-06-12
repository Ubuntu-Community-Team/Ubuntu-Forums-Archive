---
title: "epsxe: plugins/libspu.so: cannot open shared object file: No such file"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-02-03
Hello 
with epsxe, I am encountering the following error message. I followed the howto mod. and got this:
```

 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17] 
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or di
```

[http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html](http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html)

where should I get this file ?
thx

then in config for sound:
> Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",
plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetC

---

### Post by acoustibop on 2008-02-03
When you install plugins in ePSXe, frenchn00b, you need to decompress the package, put the actual plugin in the plugins folder and the configuration files in the cfg folder.  You also need to make sure permissions for these folders and their contents are correctly set.

But, if this error is occurring with the Mooby plugin, I think DoktorSeven has pointed out to you elsewhere that you don't actually need it.  I think the 2.8 version is problematic anyway.

---

