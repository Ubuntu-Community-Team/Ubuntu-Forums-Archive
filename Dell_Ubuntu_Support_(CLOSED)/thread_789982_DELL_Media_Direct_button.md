---
title: "DELL Media Direct button"
date: 2008-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rhenrick on 2008-05-11
I have Ubuntu on my laptop as my OS. No dual booting here!
I pressed my "Media Direct Button" and the music player popped up. This made me wonder if this button can be tweaked to launch other apps or do something useful. Does anyone have experience with what this button can do (besides launch Media Direct).

Thank you for your help!

---

### Post by atlas95 on 2008-05-11
The dell media direct button is "0xed" use it with gconf-editor for set the apps you want to use or simply launch the shorcut editor :)

---

### Post by rhenrick on 2008-05-11
Thanks for the info!

---

### Post by Nico0020 on 2008-05-11
I launched the gconf editor, though how to I change which program it is linked to?  I would like to probably link it with amarok.

---

### Post by fragos on 2008-05-11
apps-> metacity-> global_keybindings-> select run_command_(n)-> click disabled and enter 0xed. Next step is keybinding_commands-> command_(n) and enter application in "Value".

---

