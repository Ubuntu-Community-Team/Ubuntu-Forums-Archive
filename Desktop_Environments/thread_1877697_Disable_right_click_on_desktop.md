---
title: "Disable right click on desktop"
date: 2011-11-08
forum: Desktop Environments
---

### Post by pcarlos853 on 2011-11-08
Hi,

I am creating a thinclient using Ubuntu 10.04. When it starts up they are automatically logged in and taken to a firefox login window. From there they are able to connect to their Virtual Desktops. 

However I do not want the users to be able to right click the desktop. Is it posible to disable right click on the desktop?

Thanks,
Carlos

---

### Post by mcduck on 2011-11-08
Sure, although you will also at the same time disable the ability to have any icons on the desktop.


(and of course it should be noted that the options in right-click menu on the desktop are no different from the options available in the right-click menu of any other directory in Nautilus, so unless you've also taken the steps to prevent the users from accessing the file manager disabling the menu on desktop doesn't make much of a difference)

Anyway, all you need to do is to disable the apps/nautilus/preferences/show_desktop key in gconf. You can do that with the gconf-editor or by running the following command in a terminal:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```

The option is also available in Gnome's lockdown editor, [Pessulus]("http://linuxers.org/article/pessulus-lockdown-editor-restrictlock-stuff-you-public-gnome-desktop").

---

