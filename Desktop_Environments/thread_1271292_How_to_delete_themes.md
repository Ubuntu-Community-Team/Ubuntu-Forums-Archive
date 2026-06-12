---
title: "How to delete themes?"
date: 2009-09-20
forum: Desktop Environments
---

### Post by arnab_das on 2009-09-20
What is the procedure for deleting themes installed from gnome-look?

While installing I have used the "Install" theme option after right clicking on the change desktop background option.
However while deleting the theme from there, I find that the theme persists in the ~/.themes folder. Why is that? 

Is deleting the theme from the ~/.themes folder the proper way of deleting themes?

---

### Post by wojox on 2009-09-20
Yes that's the correct way to delete. When ever you delete or uninstall an application or what have you, It does not touch your <user> directory. That's for you to take care of.

---

### Post by benerivo on 2009-09-20
It should delete the folder from ~/.themes. If it doesn't, then it will always appear as an option every time the gnome appearances window is opened. Sometimes, when you delete a theme, there are parts of it that aren't removed, and you have to go in to the 'customize' section of gnome appearances, and delete individual components such as the window border.

Or just delete directly from ~/.themes. There's no difference.

---

### Post by arnab_das on 2009-09-20
thanks folks! much appreciated.

---

### Post by arnab_das on 2009-09-20
okay i just did something really silly!

Clearlooks apparently is installed already within Ubuntu. However I found an old thread and followed its instructions (./configure, make, make install etc.) and installed it again,

Will this cause any damage?
And is this consuming extra space on my hard disk now?

---

