---
title: "Binding keyboard shortcuts to Mouse Buttons"
date: 2008-04-22
forum: Desktop Environments
---

### Post by jesusdomingo on 2008-04-22
I tried this under System > Preferences > Keyboard Shortcuts and thought I could bind the "Show Panel Menu" action to my Middle/Right Mouse Click. But since it's "Keyboard Shortcuts", it doesn't accept mouse events.

Does ubuntu have a way of doing this? I'm using the stock configuration (fresh install) so no window manager mods yet.

Will really appreciate your help on this. Thanks!

---

### Post by warp99 on 2008-04-23
> **jesusdomingo said:**
> I tried this under System > Preferences > Keyboard Shortcuts and thought I could bind the "Show Panel Menu" action to my Middle/Right Mouse Click. But since it's "Keyboard Shortcuts", it doesn't accept mouse events.

Does ubuntu have a way of doing this? I'm using the stock configuration (fresh install) so no window manager mods yet.

Will really appreciate your help on this. Thanks!

If you install the Compiz Config Manager you can bind a plethora of actions to any of the mouse buttons of your choosing. You need to enable the universe repositories then:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by soxs on 2008-04-23
I s there another solution for binding mouse buttons to hotkey-combos? I am not really keen on being foreced to use compiz.

---

### Post by jesusdomingo on 2008-04-23
@warp99

I tried going thru the compiz settings manager but it seems that the actions already have pre-determined devices that can be used for the bindings (ie. map an action to a mouse event rather than a keyboard event).

Am I missing something?

Thanks!

---

### Post by warp99 on 2008-04-23
> **jesusdomingo said:**
> @warp99

I tried going thru the compiz settings manager but it seems that the actions already have pre-determined devices that can be used for the bindings (ie. map an action to a mouse event rather than a keyboard event).

Am I missing something?

Thanks!

If your using the CCSM (compizconfig-settings-manager) controls **not** the standard Compiz control panel in Gnome you can change the mouse button to whatever action you would like. So you can change any of the default bindings for the mouse button to a binding of your choosing, even opening programs. I change the bindings all of the time since every new version of Compiz seems to re-arrange the bindings, hot-keys, and hot-corners in spades.

Anyway if you still wanted to use a different program to set the mouse button you would still need to go into CCSM and turn off the binding for the mouse button for that event.

Edit:

In CCSM go to 'General Options' and under 'Windows Menu' choose the mouse button you would like to use. If there is a conflict between bindings CCSM will let you know and give the option of disabling the other button binding.

---

