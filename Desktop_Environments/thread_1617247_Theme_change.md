---
title: "Theme change"
date: 2010-11-09
forum: Desktop Environments
---

### Post by izghitu on 2010-11-09
Hi,

I have a customized Ubuntu 10.04 TLS Desktop running. I have all the task and tool bars removed and only icons on the desktop are left.

My question is how do I change the Theme without using the menus but by editing the config files instead? What config files do I edit to make the change?

So far I added these 2 files:
.gconf/desktop/gnome/interface/%gconf.xml
```
<?xml version="1.0"?>
<gconf>
        <entry name="icon_theme" mtime="1289225941" type="string">
                <stringvalue>gnome</stringvalue>
        </entry>
        <entry name="gtk_theme" mtime="1289225941" type="string">
                <stringvalue>Clearlooks</stringvalue>
        </entry>
</gconf>
```.gconf/apps/metacity/general/%gconf.xml
```
<?xml version="1.0"?>
<gconf>
        <entry name="button_layout" mtime="1289225941" type="string">
                <stringvalue>menu:minimize,maximize,close</stringvalue>
        </entry>
        <entry name="theme" mtime="1289227172" type="string">
                <stringvalue>Clearlooks</stringvalue>
        </entry>
</gconf>
```This changed the theme partially. The buttons and window colors and fonts changed but the window boarders(the bar from the top especially) remained the same as on the old theme.

So what config files do I need to change to completely change the theme?

Please help

---

### Post by izghitu on 2010-11-09
For those who may need this, I changed the theme by creating a launcher with the following command line:

gnome-appearance-properties %F

This opened the theme change window

---

