---
title: "ubuntu configuration windows"
date: 2006-08-04
forum: Desktop Environments
---

### Post by sunitham on 2006-08-04
In most of the ubuntu configuration windows, there are no Ok and Cancel buttons. There is only one Close button. So, whatever changes I make is automatically saved. There is no way for me to go back to my previous settings by cancelling it.

Please suggest

---

### Post by mlind on 2006-08-04
> **sunitham said:**
> In most of the ubuntu configuration windows, there are no Ok and Cancel buttons. There is only one Close button. So, whatever changes I make is automatically saved. There is no way for me to go back to my previous settings by cancelling it.

Please suggest

That's sad, but true fact of some GNOME dialogs :( 
IMO it's a bad design not allowing user to revert their changes which often leads to broken system configuration.

You can file bugreports about packages that contain these configuration windows to Ubuntu [launchpad.net]("https://launchpad.net/distros/ubuntu")

---

### Post by mlind on 2006-08-04
> **sunitham said:**
> In most of the ubuntu configuration windows, there are no Ok and Cancel buttons. There is only one Close button. So, whatever changes I make is automatically saved. There is no way for me to go back to my previous settings by cancelling it.

Please suggest

That's sad, but true fact of some GNOME dialogs :( 
IMO it's a bad design not allowing user to revert their changes which often leads to broken system configuration.

You can file bugreports about packages that contain these configuration windows to Ubuntu [launchpad.net]("https://launchpad.net/distros/ubuntu")


(Most of the settings are stored as gconf keys, so you can revert to defaults using gconftool-2 --recursive-unset, but you need to know what value the information is keyed against..)

---

