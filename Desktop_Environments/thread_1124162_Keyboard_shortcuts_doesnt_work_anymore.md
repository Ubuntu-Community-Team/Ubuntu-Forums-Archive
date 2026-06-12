---
title: "Keyboard shortcuts doesnt work anymore"
date: 2009-04-13
forum: Desktop Environments
---

### Post by Lomz on 2009-04-13
After an upgrade to 9.04 the keyboard shortcuts doesnt work anymore, it also looks like there has been some changes to the keyboard-settings-feature, anyone who knows how to help me?

---

### Post by Lomz on 2009-04-14
bump

---

### Post by ltcmdata on 2009-04-24
same problem here.
in the shortcuts the alt key was changed to meta.after correcting this the shortcuts worked for a while, but after a reboot stopped functioning entirely.

---

### Post by ltcmdata on 2009-04-24
ok got it.only needed to run xfce4-settings-helper :lolflag:

---

### Post by ftmichael on 2009-04-24
I'm having the same problem with Ubuntu (not Xubuntu).  **gconf-editor** says my keybinding settings are still as they were, but since upgrading to Jaunty they just plain don't work.  Pressing the correct key combo yields no output.

If **xfce4-settings-helper** is the magic fix in Xfce, what's the magic fix in Gnome?

---

### Post by mtnwalker2b on 2009-04-24
> **ftmichael said:**
> I'm having the same problem with Ubuntu (not Xubuntu).  **gconf-editor** says my keybinding settings are still as they were, but since upgrading to Jaunty they just plain don't work.  Pressing the correct key combo yields no output.

If **xfce4-settings-helper** is the magic fix in Xfce, what's the magic fix in Gnome?


Same problem here-  is any information available?

---

### Post by vivinc on 2009-04-26
Hi,
i had the same problem and then I just installed ccsm (sudo apt-get install compizconfig-settings-manager) and then enabled the first plugin (than it should be named "Commands" or something like that).

Hope this will help you.

Bye!

---

### Post by noiq on 2009-04-27
For me the solution was to remove all multiple occurrences of definitions (same "value" value) in *$HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml*, which were not set by myself. Now my shortcuts work fine again.

---

