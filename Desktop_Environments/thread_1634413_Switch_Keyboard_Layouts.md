---
title: "Switch Keyboard Layouts"
date: 2010-11-30
forum: Desktop Environments
---

### Post by White_Owl on 2010-11-30
I am using Gnome 2.32 (Ubuntu 10.10 /x64 ). 
By using the supplied keyboard configuration utility I successfully set up two language layouts and they work perfectly. 
Since I also often work on Windows and default shortcut to switch layouts in it is Alt+Shift (and after many years I am very used to this), I tried to setup the same shortcut in Gnome. 
But with a Gnome I have a problem: once I press Alt+Shift - layouts switch immediately and I am unable to do Alt+Shift+<Something> shortcuts. 

So my main question is: 
Is it possible to teach Gnome's keyboard layout switcher to do the actual switch of layouts only if I press and release the Alt+Shift combination without touching any other keys?

---

### Post by grahammechanical on 2010-11-30
As Keyboard Preferences Options does not give that option, I would say No. But then what do I know?

Regards.

By the way. I like the way I can change to another language so easily.

---

### Post by Krytarik on 2010-11-30
You may use the command/keybindings-capabilities of Compiz for example. I have just found out what command one has to use to change the keymap to a specific one, examples are:

```
setxkbmap us
setxkbmap de
```

In order to get the shortnames of the keymaps you use, you enter the following command in a terminal:

```
gconftool -g /desktop/gnome/peripherals/keyboard/kbd/layouts
```

To set up the bindings, you go to "System -> Preferences -> CompizConfig Settings Manager -> Commands" (assuming you have it installed already). On tab "Commands", you enter the respective commands; on the tab "Key Bindings" you set up the keyboard-shortcuts you want to use, of course you can also use the mouse-button- or edge-bindings (personally I find the edge-bindings very useful).

---

