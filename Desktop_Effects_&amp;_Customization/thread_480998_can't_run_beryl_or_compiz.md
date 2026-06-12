---
title: "can't run beryl or compiz"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by oliviacond on 2007-06-22
i'm using fglrx and xgl.
i just switched from GNOME to KDE.
the only problem is the desktop effect not working anymore.
I tried to install aquamarine for the beryl, the error message is "no compatible windows decorator"
so i try to install compiz-kde by using this guide : [http://compiz.org/Ubuntu_Installation_Guide](http://compiz.org/Ubuntu_Installation_Guide)
this is the error message i got :
```

$compiz
/usr/bin/compiz.real: No composite extension
/usr/bin/compiz: 47: metacity: not found

```

my xorg :
```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"dbe"
EndSection
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"DRI"			"true"
	Option		"ColorTiling"		"on"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod" 		"EXA"
	Option		"XAANoOffscreenPixmaps"
EndSection

```


Anyway,
i found this : [http://compiz.org/Patch_to_make_XGL_faster](http://compiz.org/Patch_to_make_XGL_faster)
any idea how to patch XGL?

---

### Post by oliviacond on 2007-06-22
ok, i was able to run compiz with the help of these two posts:
[http://ubuntuforums.org/showthread.php?t=417865](http://ubuntuforums.org/showthread.php?t=417865)
[http://forum.compiz.org/viewtopic.php?t=239](http://forum.compiz.org/viewtopic.php?t=239)

but...... i can't load kde windows decorator
```

$ compiz --replace gconf &
[1] 5516
$ compiz.real: Couldn't load plugin 'gconf'
$ kde-window-decorator --replace &
[1] 5546

```

my glxinfo
```
$ glxinfo | grep texture_from_pixmap
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,

```

---

