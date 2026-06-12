---
title: "Editing Main Menu in Unity"
date: 2012-04-21
forum: Desktop Environments
---

### Post by lads on 2012-04-21
Hello everyone,

Today I tried to change the settings of one of the icons in the launcher and couldn't do it. In fact, I'm presently unable to do any sort of operation in the Main Menu: changing the properties of an existing item, creating a new item or a new menu, nothing happens when I click these buttons/menus. What's amiss here? Some permission issue? Is there any way I can edit the Main Menu through the command line?

Thank you for reading.

---

### Post by Frogs Hair on 2012-04-21
You should be able to edit the main menu. I created a number of launchers and changed icons many times on 11.10 . I don't know the source of the problem though . I am unable to open the main menu from the command line on 12.04 but the GUI works as it did on 11.10. I'm not aware of any elevated permissions needed to edit menus but you could try from the administrator account.

---

### Post by forsubhi on 2012-04-21
Do you try reinstalling the program

---

### Post by Krytarik on 2012-04-21
Please see my earlier post here:

[http://ubuntuforums.org/showthread.php?p=11604556#post11604556](http://ubuntuforums.org/showthread.php?p=11604556#post11604556)

Regards.

---

### Post by lads on 2012-05-07
Thank you Krytarik, installing the gnome-panel package solved the issue. For future reference here is the command:

```
sudo apt-get install --no-install-recommends gnome-panel
```

---

