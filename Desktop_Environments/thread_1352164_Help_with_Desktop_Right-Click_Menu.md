---
title: "Help with Desktop Right-Click Menu"
date: 2009-12-11
forum: Desktop Environments
---

### Post by unklbeemer on 2009-12-11
Using Xubuntu 9.10.

Does anyone know how to get rid of the "Desktop Settings..." and "Properties..." part of this right-click menu? Is there a configuration file for this right-click menu? (See Attachment Below)

---

### Post by jollysnowman on 2009-12-11
Here you go: 

[http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu](http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu)

Short version: use xfce4-menueditor for convenience, but to remove those items you're talking about, I'd just edit the xml itself.

---

### Post by unklbeemer on 2009-12-11
Xubuntu 9.10 uses XFCE 4.6. Correct me if I am wrong, but didn't they change the way they used the configuration files? There is no menu.xml in the /xdg/xfce4/ directory

Unless I am missing something?

---

### Post by jollysnowman on 2009-12-11
You're right.... I didn't notice that (I know it says I use Xubuntu 9.10, but I switched to CrunchBang and Xubuntu is sitting idle right now).

I poked around, and found an XML in ```
/etc/xdg/menus/xfce-applications.menu
```

---

### Post by unklbeemer on 2009-12-11
First of all, thank you for your quick responses to me. However, the xfce-applications.menu file, which I edited earlier, only edits the application menu found in the panel and (if selected) found in the right-click menu. I have edited that xml file to scale down the application menu to include only the things I want (or rather to take out the things I don't). This file, at least from what I understand, doesn't effect the other items in that right click menu. It only effects the applications menu.

---

### Post by jollysnowman on 2009-12-11
Ah, ok. Maybe I should think before I respond haha.

---

### Post by XubuRoxMySox on 2009-12-11
It is not ordinarily possible to edit that menu, but I've read that a menu editor is coming in the next updated version of Xfce. Definitely worth the wait. In the meantime it's easy enough with the right-click on the screen in Xubuntu.

-Robin

---

