---
title: "beryl works but what are these errors?"
date: 2007-02-19
forum: Desktop Environments
---

### Post by m.musashi on 2007-02-19
I have been using beryl for months now without any real problems. For fun, I launched beryl-manager in a terminal and got a bunch of errors. It still works but I'm wondering if these are something I should be worried about and fix or if it's just characteristic of beryl. Anyway, here is the output.
```
(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:4969): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:5034): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
**************************************************************
* Beryl system compatibility check                           *
**************************************************************
Engine settings loaded

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
Initiating splash
```
I'm also wondering why after all the errors (really warnings I guess) that beryl has to relaunch.
```
Relaunching beryl with __GL_YIELD="NOTHING"
```
And what that means.

Thanks.

---

### Post by jackhynes on 2007-02-26
I'm also confused about this - but for me it seems to happen in everything I open with the terminal including gconf-editor and gedit. I do use beryl.

---

### Post by m.musashi on 2007-02-26
My question pretty much died a silent death. I don't know if that means no one knows or no one cares. My system seems to work fine but it is kind of annoying that these errors exist. I'd like to fix whatever is causing them if possible.

---

### Post by amphet on 2007-02-26
see if this works

[http://ubuntuforums.org/showthread.php?t=330757]("http://ubuntuforums.org/showthread.php?t=330757")

---

### Post by FuturePilot on 2007-02-27
```
Relaunching beryl with __GL_YIELD="NOTHING"
```
I'm pretty sure that is normal as I get that too. And there's even an option in the Beryl Manager to activate that option manually. Something to do with trouble shooting.

---

### Post by m.musashi on 2007-03-01
> **amphet said:**
> see if this works

[http://ubuntuforums.org/showthread.php?t=330757]("http://ubuntuforums.org/showthread.php?t=330757")

Thanks. That might if fixed it as well as some other theme related errors.

---

