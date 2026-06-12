---
title: "Error loanding Human theme
Can't open file /usr/share/gdm/themes/Human/Human.xml"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by pininy on 2007-08-02
Hi,

Right after installing Gusty from Feisty, my login screen always points to the old feisty-gdm-theme, anyway of getting rid of the annoying dialog?

many thanks! 

Error loanding Human theme
Can't open file /usr/share/gdm/themes/Human/Human.xml

---

### Post by virilc on 2007-10-31
Have you tried reinstalling the themes?

```
sudo apt-get remove feisty-gdm-themes
sudo apt-get install feisty-gdm-themes
```

By the way, I found the Human.xml file by issuing:

```
dpkg -S Human.xml
```

Very useful on searching for dependencies/specific files. :) If it won't work, most probably it's a bug that needs to be reported? :confused:

---

