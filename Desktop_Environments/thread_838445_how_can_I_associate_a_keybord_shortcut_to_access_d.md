---
title: "how can I associate a keybord shortcut to access desktop"
date: 2008-06-23
forum: Desktop Environments
---

### Post by lavy on 2008-06-23
Hy,


I'm trying to associate a keyboard shortcut key to Desktop access. I mean I want to minimize all windows by a stroke of a key and see the desktop. I've looked in System Settings -> Keyboard -> Keyboard Shortcuts but I didn't find what I wanted.

Thanks

---

### Post by VMC on 2008-06-23
> **lavy said:**
> Hy,


I'm trying to associate a keyboard shortcut key to Desktop access. I mean I want to minimize all windows by a stroke of a key and see the desktop. I've looked in System Settings -> Keyboard -> Keyboard Shortcuts but I didn't find what I wanted.

Thanks

Look at the bottom far left. There shold be a square box. If you hover over it, it says "Click here to hide all windows and show the desktop"

Edit: If you don't have it, the right click on one of the panels and use +Add to the panel. Look for Show Desktop, then add it.

---

### Post by rainwalker on 2008-06-23
Try Control + Alt + D
If that doesn't work, are you using Compiz? If so, install the compizconfig-settings-manager package and then go to System > Preferences > Advanced Desktop Effects Settings. Under the General Options sections, go to the Key Bindings tab and look at what is set to show the desktop

---

### Post by jspolen on 2008-06-23
Found this guide at [http://ubuntu.wordpress.com/2006/01/30/defining-keyboard-shortcuts-for-commands/]("http://ubuntu.wordpress.com/2006/01/30/defining-keyboard-shortcuts-for-commands/")



    1) Run gconf-editor
    2) Find Apps -> Metacity -> Keybinding Commands
    3) Click on command_1 -or any empty one upto- command_12
    4) In “value” type the command you want to run
    5) Move upto “global_keybindings”
    6) Click on “run_command_x (x corresponds to the value at 3)
    7) Type in a key or combination, eg:
    Super_L = Left Win key
    Super_R = Right Win key 8) It should work straight away

To find a value of a key, run: gnome-keybinding-properties and click in an unused box then press the key you want. Just press backspace to clear it before you quit if you don’t want to save it.

---

### Post by lavy on 2008-06-24
Hy,

I forget to mention that I use KDE, anyway the Ctrl+Alt +D shortcut worked.

Tx

---

### Post by bogdanbiv on 2008-06-28
AFAIK, Kubuntu = Ubuntu + KDE Desktop Env
I don't see where the gconf-editor or Metacity fit in the Kubuntu enviroment.

I guess there's some misunderstanding here.

---

