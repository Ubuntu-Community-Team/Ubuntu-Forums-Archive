---
title: "Alt + F2 dialog package"
date: 2010-02-25
forum: Desktop Environments
---

### Post by silent_n0va on 2010-02-25
Which package is the Alt + F2 run dialog in? I have GNOME on Gentoo and the key combination doesn't work...using gnome-do in its place.

---

### Post by mcduck on 2010-02-25
> **silent_n0va said:**
> Which package is the Alt + F2 run dialog in? I have GNOME on Gentoo and the key combination doesn't work...using gnome-do in its place.

It's a feature provided by the gnome-panel. (I have no idea what's the actual package that includes the panel, though).

---

### Post by zlatkart on 2010-02-25
> It's a feature provided by the gnome-panel. (I have no idea what's the actual package that includes the panel, though). 	

I'm quite sure that it's metacity. I'm running openbox with gnome-panel and I don't have ALT+F2

---

### Post by mcduck on 2010-02-25
> **zlatkart said:**
> I'm quite sure that it's metacity. I'm running openbox with gnome-panel and I don't have ALT+F2

no, it definitely is Gnome-panel. If you replace Metacity in Gnome with anything else (for example with Compiz, like so many Ubuntu user's do) the Run dialog still works, but if you kill the panel the dialog stops working.

The dialog used to be a separate program, started by running "gnome-run", but it was integrated into gnome-panel in Gnome 2.6.

If the shortcut isn't working for you you are probably missing the Gnome component that handles keyboard shortcuts, or the relevant gconf key isn't set or something.

edit: This will probably help you: [http://openbox.org/wiki/Help:GNOME/Openbox]("http://openbox.org/wiki/Help:GNOME/Openbox")
```
<keybind key="A-F2">
    <action name="execute"><execute>gnome-panel-control --run-dialog</execute></action>
</keybind>

```

---

### Post by zlatkart on 2010-02-25
Cool
Thank you. But strange as I think that killing Metacity always killed ALT+F2 (as far as I remeber). Anyway...

---

### Post by silent_n0va on 2010-02-25
I have Metacity and gnome-panel both on Gentoo, though it's running Compiz currently. Strange that the run dialog wouldn't work with Compiz as it works brilliantly in Ubuntu, but I will check on my key bindings tonight.

---

### Post by m_duck on 2010-02-25
If Compiz is running, I believe there is a "Gnome Compatibility" plugin (or similar) which must be enabled to allow Alt+F2 and some other bits to work again. Having said that, if it wasn't working before Compiz was enabled, this may not be the case.

---

### Post by silent_n0va on 2010-02-25
Gnome compatibility was turned off. Turned it on and now the dialog runs. ^_^

---

