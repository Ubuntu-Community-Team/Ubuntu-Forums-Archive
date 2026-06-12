---
title: "adding items to top menu-bar in bash command line interface ubuntu 10.10"
date: 2011-01-13
forum: Desktop Environments
---

### Post by AdmiralNotorious on 2011-01-13
hello again. 

i am making a customization script and i need some help again. I would like to include my gnome menu-bar customization in the script.Does anyone know how to add and remove menubar items in gnome from a command line??

---

### Post by 3Miro on 2011-01-13
Check the configurations files for .gnome, .gconf, .config in your /home/your_user_name file. Those contain all the configuration files for Gnome, however, your script will have to edit them "manually".

You can look into gconf-editor, I think it has nice CLI features.

---

### Post by AdmiralNotorious on 2011-01-13
excuse me again, but im having trouble finding my way around the gnome config files. are you certain the answer lies with them, and if so, how do i "manually" edit them?

---

