---
title: "Compiz fusion and window decorations..."
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by fjf on 2007-07-01
In Feisty, with nvidia 6600 gt enabled, I get no decorations and blank terminals when I open them.  The command compiz --replace in a terminal gives many lines of (likely) working stuff, but it finalizes with the errors:


GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing ring options...done
Initializing zoom options...done
Initializing place options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
Initializing scale options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:31924): Wnck-WARNING **: Unhandled action type (nil)

Any ideas?.

---

### Post by autocrosser on 2007-07-01
If you have had Beryl installed in the past you can try my fix. Look at:

 [http://ubuntuforums.org/showthread.php?p=2945994#post2945994](http://ubuntuforums.org/showthread.php?p=2945994#post2945994)

---

### Post by steveneddy on 2007-07-01
Is Emerald installed?

Try 

```
emerald --replace&
```

---

### Post by fjf on 2007-07-01
The howto I followed indicated to uninstall first beryl and emerald.  I already did a search and tried all those --replace combinations.  Don't work.  I reinstalled emerald and tried the compiz --replace -c emerald --replace.  No luck.

---

### Post by steveneddy on 2007-07-01
Did you see this

[http://ubuntuforums.org/showthread.php?t=489341](http://ubuntuforums.org/showthread.php?t=489341)

---

### Post by fjf on 2007-07-01
Just tried the script and got the same errors listed above, and no decorations.

---

### Post by fjf on 2007-07-01
YESSSSSSSSSSSSSSSS!.  Just got it working!!.  It is all here:
[http://ubuntuforums.org/showthread.php?p=2946778#post2946778](http://ubuntuforums.org/showthread.php?p=2946778#post2946778)

Editing the xorg.conf file and adding to the device section:

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

And adding to the end of the file:

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Don't have a clue of what this does, but it makes a nvidia 6600GT work with compiz fusion.

Thanks to everyone.

---

