---
title: "Gnome3 Freezing Randomly"
date: 2011-12-18
forum: Desktop Environments
---

### Post by Scyntherei on 2011-12-18
My issue is that Gnome 3 will work fine for hours on end then suddenly freeze to the window I currently have select and ignore all keyboard/mouse interaction. (It's frozen to firefox at the moment.) This has become a major annoyance because it does not resolve itself when restarting the shell, only upon reboot. Sometimes the terminal command (ctrl+alt+t) works then I kill/restart the shell, only to have it freeze to the next window I select. When rebooting it works again for hours. It either occurs after extended use or while playing music (Can't determine which since its only done it after a long period and while a media player was open.). Any tips on how to resolve this? or If it's a known issue?

[lspci Output]("http://pastebin.com/1GWKHdnL")

Painfully managed to capture terminal output AND save it. xD
> tyler@tyler-OEM:~$ killall gnome-shell
tyler@tyler-OEM:~$ gnome-shell
(gnome-shell:11141): folks-DEBUG: individual-aggregator.vala:305: Setting primary store IDs to defaults.
(gnome-shell:11141): folks-DEBUG: individual-aggregator.vala:333: Primary store IDs are 'eds' and 'system'.
      JS LOG: GNOME Shell started at Sun Dec 18 2011 21:12:33 GMT-0600 (CST)

(firefox:11174): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:11174): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:11174): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:11174): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:11222): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:11222): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:11222): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:11222): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
      JS LOG: pushModal: invocation of begin_modal failed
      JS LOG: pushModal: invocation of begin_modal failed
      JS LOG: pushModal: invocation of begin_modal failed
      JS LOG: pushModal: invocation of begin_modal failed
      JS LOG: pushModal: invocation of begin_modal failed


---

### Post by Frogs Hair on 2011-12-19
Is this with all themes ?  Pixmap is not installed on my installation because I have no themes that use it or require it .

---

### Post by Scyntherei on 2011-12-19
I'm using the [Ambience Dark]("http://gnome-look.org/content/show.php/Ambiance+Dark?content=147513") theme. I didn't have pixmap installed either, but I just installed it. See if that clears it up.. If not, back to a default theme and see if it works I suppose.

EDIT: Right alt + sys req + k then logging back in seems to remedy it... Losing the session is kind of annoying though...

---

