---
title: "changing Keyboard Shortcuts, when super key is press it inputs &quot;win+L&quot;"
date: 2009-05-28
forum: Desktop Environments
---

### Post by Iztari on 2009-05-28
Every time I try to change a keyboard shortcut to something like "win+key", no matter what key I press after 'win' it inputs 'Win+L' or if I only hit the 'win' key. This only happens when changing shortcut in 'System->Preferences->Keyboard Shortcuts'. How could I fix this? 


Thanks in advance for the help.

---

### Post by Locutus_of_Borg on 2009-05-28
try xmodmap

---

### Post by VCoolio on 2009-05-28
You can set the keybinding manually in the configuration editor. Open it (it's in the applications menu somewhere; you can also do alt+f2 and type gconf-editor) and navigate to apps->metacity->global_keybindings. Here you can set the bindings manually. They correspond to the commands set in keybinding_commands. For the super/windows-key enter <mod4>. 

Read more [here]("http://ubuntuforums.org/showthread.php?t=1171209").

---

### Post by Iztari on 2009-06-13
I don't know exactly what fixed it (I did try most of the you suggested), but it seems to be working. All I know is that now it works and when I press the win key in the keyboard shortcuts it now comes up as Mod4.

Thanks for the help!:P

---

