---
title: "Gconf Config Editor"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jenkins_t on 2006-02-21
> well, you can try making a .splash directory in your home folder,and drag all the splashes you like in it.
Then, in Applications->System->Gconf Config Editor, go to apps->gnome-sesion->options
click on splash image, the field is open for editing. Type in /home/*username*/.splash/*splash_picture's_name.png*

I dont have this Gconf Config Editor in my menu. Where can I find it?

---

### Post by codejunkie on 2006-02-21
[QUOTE=jenkins_t]I dont have this Gconf Config Editor in my menu. Where can I find it?[/QUOTE]
open a terminal and enter ```
gconf-editor
```this should open the configuration editor you can also right click on the Applications menu choose Edit Menus scroll down to the system tools section and make sure the Configuration Editor box is checked.

---

