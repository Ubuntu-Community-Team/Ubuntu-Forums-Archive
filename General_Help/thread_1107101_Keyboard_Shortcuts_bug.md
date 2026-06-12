---
title: "Keyboard Shortcuts bug"
date: 2009-03-26
forum: General Help
---

### Post by cristian.vrabie on 2009-03-26
Hi guys,
I recently moved to Ubuntu 8.10 / gnome 2.24.1 from Windows.
I tried to edit some of the keyboard shortcuts with some that I'm more used to. I did this by going to System -> Preferences -> Keyboard Shortcuts. Everything works fine until I try to use the Super (windows logo) key. It seems that every combination I try to add (like super + D or super + E) is detected as super + L (which I already assigned to screen lock). This seems like a bug because if I try to assign a similar key combination in a program (like Eclipse) it works fine.
Is there a file that stores these key combinations that I can manually edit in order to do the key bindings I want to?
Thanks!
Cristian

---

### Post by ryanhaigh on 2009-03-27
I despise the keyboard shortcut tool that gnome provides because of the way it 'handles' the super/windows key. You can edit the shortcuts manually using gconf-editor. Just press alt-f2 and enter
```
gconf-editor
```
I am on a windows machine at the moment so I can't confirm but I believe the settings you are looking for are under something like apps>metacity>global keybindings.

I'm not sure if these will work if you are using compiz, in which case you will likely need to use the compiz settings manager.

---

