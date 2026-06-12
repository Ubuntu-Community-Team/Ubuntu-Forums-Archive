---
title: "My Trash Can Missing"
date: 2012-11-26
forum: Desktop Environments
---

### Post by vkadal on 2012-11-26
Previously my trash can will be in the desk top. Later I installed Tamil keyboard, and the keyboard switch Icon taken the place of my Trash can. Since that that day, I could not locate the can. I want to restore some files which I deleted earlier. I am using ubuntu 10.04.

Those who help to restore my trash can, can share the contents

Thanks in advance

---

### Post by ajgreeny on 2012-11-26
The trash is at ~/.local/share/Trash, hidden in your home.  If you open up nautilus then hit Ctrl+L and type trash:/// in the box it will take yo to the trashbox from where you can use the right click and Restore option.  You can even make a link to it on the desktop by right clicking then with command **nautilus trash:///** in the box you fill in manually.

It should, however, be an option in gconf-editor, which you can install if it is not already installed, and then go to apps->nautilus->desktop where you can select to show the icon and the name it should use.

---

