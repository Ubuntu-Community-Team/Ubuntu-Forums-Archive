---
title: "i deleted my  menu items"
date: 2008-01-29
forum: Desktop Environments
---

### Post by liakosantonios on 2008-01-29
hi to all,

after giving this command "sudo rm -r skype.desktop /usr/share/applications" i lost almost all of my menu items, can anyone help me to restore them?
i have only Applications=>Internet=>Fire starter and System=>Administration=>Login Window
i have no idea.....

how can i restore the default menu?

---

### Post by jryprt on 2008-01-29
> **liakosantonios said:**
> hi to all,

after giving this command "sudo rm -r skype.desktop /usr/share/applications" i lost almost all of my menu items, can anyone help me to restore them?
i have only Applications=>Internet=>Fire starter and System=>Administration=>Login Window
i have no idea.....

how can i restore the default menu?

Right click on the top panel go to Add to Panel click it & look for Main Menu.

---

### Post by urukrama on 2008-01-29
liakosantonios, the command you used deleted the /usr/share/applications and all its subfolders. If you wanted to delete only the skype.desktop file, you should have used sudo rm /usr/share/applications/skype.desktop  instead. It is always advisable to know what commands you use. Ask whoever gives you a command what it does and read the man pages (man *application*) to find more about the command.

How to restore what you did? You could use alacarta to recreate the menu (Alt+F2 and type alacarte), or recreate all the desktop files for all your application in  /usr/share/applications/ (quite a task if you have a lot of applications). Alternatively, you could reinstall your applications (sudo aptitude reinstall *application*), making sure first you saved all your configuration files (if you made systemwide changes to the configuration and don't want to make them again).


> **jryprt said:**
> Right click on the top panel go to Add to Panel click it & look for Main Menu.

That probably won't make a difference if (s)he deleted /usr/share/applications

---

