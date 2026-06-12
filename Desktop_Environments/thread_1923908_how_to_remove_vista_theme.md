---
title: "how to remove vista theme"
date: 2012-02-11
forum: Desktop Environments
---

### Post by ramitwadhwa on 2012-02-11
i have installed vista theme on 11.04. now I have upgraded to 11.10 and I want to remove the vista theme and get the default ubuntu theme.

the default icons are missing, and

---

### Post by Frogs Hair on 2012-02-11
How was it installed ? Normally removing the folder from home/hidden folders/.themes or file system/usr/share/themes does the trick .

If the theme had an installation script check for removal instructions at site where you found the theme . The fact that you have upgraded from Gnome 2 to Gnome 3 may complicate things .

You also need to install advanced setting from the software center to change themes in 11.10.

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by bluexrider on 2012-02-11
> **ramitwadhwa said:**
> i have installed vista theme on 11.04. now I have upgraded to 11.10 and I want to remove the vista theme and get the default ubuntu theme.

the default icons are missing, and
Congrats. I am surprised that the upgrade actually allowed the present theme to remain installed.

If you did a full upgrade and installed everything needed then reset unity.

To reset Unity in CompizConfig Settings manager, open a terminal or press ALT + F2 and enter the following command. ```
unity --reset
```

Similarly, to reset Unity Launcher icons, use the following command.
 ```
unity --reset-icons
```

---

