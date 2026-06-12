---
title: "window manager problems"
date: 2005-07-19
forum: Desktop Environments
---

### Post by Digitallysick on 2005-07-19
I use kde as my default, recently my pc now boots to gnome, instead of kde, i have to alt ctrl backspace , then select KDE, it will not let me choose it as default, in the manager menu i no longer see the radio buttons, its all greay, i just click kde, and have to login, id rather it go straight to kde, please help me!

---

### Post by Xian on 2005-07-19
Which display manager are you using...gdm or kdm?

---

### Post by Digitallysick on 2005-07-20
gdm, i dont know the difference between the 2, but in  the gnome menu, when logging out, you can't even see the radio buttons, at all, its very odd

---

### Post by Mr Frosti on 2005-07-20
You can change which display manager you want to come up as default by running the following command:

```
sudo gedit /etc/X11/default-display-manager
``` 

Type in the path of the display manager you want to come up by default on your computer.

For **G**nome **D**isplay **M**anager, type: "/usr/bin/gdm"

For **K**DE **D**isplay **M**anager, type: "/usr/bin/kdm"

Save the changes, and then restart Xorg by pressing "Ctl + Alt + Backspace". This should reflect the changes you have just made.

---

