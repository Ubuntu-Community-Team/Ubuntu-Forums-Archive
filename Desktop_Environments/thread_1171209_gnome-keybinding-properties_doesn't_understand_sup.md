---
title: "gnome-keybinding-properties doesn't understand super key"
date: 2009-05-27
forum: Desktop Environments
---

### Post by neerolyte on 2009-05-27
Hi,

I've been trying to set some keyboard shortcuts that use the super key (aka the windows key) via gnome-keybinding-properties and not getting anywhere.

gnome-keybinding-properties seems to treat the super keys as non-modifier keys so I can't put in codes like Super+V as the dialog decides I'm done entering my value as soon as I hit the super **modifier** key.

I also tried editing the same shortcuts via gconf as suggested at [http://ubuntuforums.org/showthread.php?t=596961](http://ubuntuforums.org/showthread.php?t=596961) with no luck. Has the format changed since that thread?

I can get shortcuts working via either method as long as I don't use the super key, but I want to use the super key so this is very frustrating :/

---

### Post by VCoolio on 2009-05-27
Hi, you received no answer yet, so either it rather difficult or it's plain obvious and we both are blind to it. Anyway, I recommend xbindkeys, a little app that you can use for keybindings (or even keys and mousebuttons combined). After running 'xbindkeys --defaults > $HOME/.xbindkeysrc' it will create the file .xbindkeysrc in your homefolder, in which you can assign key bindings by adding lines like this (first command between "", then indented line with keybinding; super key = mod4):
```
"gnome-open http://www.ubuntuforums.org"
   mod4 + shift + u
"gnome-terminal"
  control + dead_grave
```
You can also use gui for editing key bindings (install xbindkeys-config, make sure you have NumLock disabled when assigning key bindings or it won't work). There is more to find eg. [here]("http://www.linux.com/archive/feature/59494"), or google it.
The keys are called like this: Control, Shift, Mod1 (=Alt key), Mod2 (=NumLock key), Mod3 (= CapsLock key), Mod4 (Super/winkey), Mod5 (Scroll).

---

### Post by neerolyte on 2009-05-28
You just gave me the answer for getting it working in gconf, thanks!

The correct shortcut for win+r in gconf is "<Mod4>r" not "<Super_L>r" or "<Super>r" like I had been trying.

---

### Post by ORBstacle on 2009-10-31
Hey, I don't know if this is the right topic for this exactly, but basically i was trying to use the document flip button on my Logitech MX518, to open expo, but i was having difficulty making the .xbindkeysrc work with the super key, i could probably have changed the shortcut for expo, but anyway, i found this after hours of searching:

```
"xte 'keydown Super_L' 'key e' 'keyup Super_L'"
    m:0x0 + b:10 
```

PS: just for the sake of completeness, you will probably need to follow this guide on how to edit /etc/X11/xorg.conf (or something similar) to allow all of the mouse buttons to be detected: [http://ubuntuforums.org/showthread.php?t=606610]("http://ubuntuforums.org/showthread.php?t=606610")

---

### Post by manech on 2012-05-01
Using **<Mod4> in gconf-editor** instead of <Super> also worked for me, but in addition I needed to choose one of the options "**Hyper is mapped to Win-keys**" or "**Meta is mapped to Win-keys**" instead of the "Default" behavior.
(The option can be found in gnome-control-center > Keyboardlayout > Options > Alt/Win key behavior.)

---

