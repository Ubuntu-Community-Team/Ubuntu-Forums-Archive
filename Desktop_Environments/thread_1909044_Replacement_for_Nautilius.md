---
title: "Replacement for Nautilius?"
date: 2012-01-14
forum: Desktop Environments
---

### Post by matza55 on 2012-01-14
Someone who had tip? I have used Gnome Commander, and it's good. Is there a way to set it for standard?

---

### Post by IWantFroyo on 2012-01-14
Are you just asking for suggestions?
If so, my favorite is Thunar.
To make it the default file manager:
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by Krytarik on 2012-01-14
You could try to adapt the instructions in this guide to your specific case:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

However, if you are aiming for something more light-weight than Nautilus, I'd rather suggest Thunar. I, too, use Gnome Commander for some few tasks, but I wouldn't use it as the default file browser.

Regards.

EDIT: Hehe, *IWantFroyo* beat me in the last second! :P

---

### Post by MooPi on 2012-01-14
I use pcmanfm , which stands for "PC man file manager".
It allows for for opening terminal from the directory that is in use, and is extremely light weight.

---

### Post by I_can_see_the_light on 2012-01-14
> **matza55 said:**
> Someone who had tip? I have used Gnome Commander, and it's good. Is there a way to set it for standard?

You can press Alt+F2 and enter ```
gedit .local/share/applications/mimeapps.list
```
Inside it, under the section named **[Default Applications]** you can enter ```
inode/directory=gnome-commander.desktop
```I don't have Gnome Commander installed myself so I'm not sure if the .desktop file is really called gnome-commander.desktop. To find that out you can enter this command in a terminal:
```
ls /usr/share/applications/ | grep -i commander
```

---

### Post by matza55 on 2012-01-15
Thank you all for the great help!!

---

