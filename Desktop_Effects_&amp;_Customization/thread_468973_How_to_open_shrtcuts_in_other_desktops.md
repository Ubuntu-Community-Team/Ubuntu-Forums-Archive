---
title: "How to open shrtcuts in other desktops"
date: 2007-06-09
forum: Desktop Effects &amp; Customization
---

### Post by bobojones on 2007-06-09
I was wondering if there was a way to stipulate which virtual desktop a shortcut open in.

Thanks
J

---

### Post by thelinuxguy on 2007-06-09
Not exactly but there is Wmctrl. It will help you move a window to a desktop. Or you can write a script which includes lines to
1) Change to the virtual desktop
2) Launch the program
3) Change back to the desktop you were using

I haven't tried it and can't list any exact steps. If you get it working, do post back.

[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/)
[http://origin.arstechnica.com/articles/columns/linux/linux-20050804.ars/2](http://origin.arstechnica.com/articles/columns/linux/linux-20050804.ars/2)


Edit: 
Its available in the repository
```

sudo apt-get install wmctrl 

```

This script launches nautilus on the second desktop and switches to the first desktop:
```

wmctrl -s 1
nautilus
wmctrl -s 0

```

Edit:
Seems to be working. No need to create a script file for every launcher you create.
To launch a program (say nautilus) on the second desktop, create a launcher and in the command textbox type:
```

bash -c "wmctrl -s1 && nautilus && wmctrl -s0"

```

I guess this is more like what you wanted.

---

