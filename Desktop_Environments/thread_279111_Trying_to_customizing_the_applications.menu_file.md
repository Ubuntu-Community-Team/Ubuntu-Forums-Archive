---
title: "Trying to customizing the applications.menu file"
date: 2006-10-17
forum: Desktop Environments
---

### Post by tflanders on 2006-10-17
I am trying to change the applications menu to say Apps instead of the word Applications.

Example menu below:

Apps  Places  System

or something like that.

I tried to edit these 3 files
/etc/xdg/menus/applications.menu
/home/username/.config/menus/applications.menu
/usr/share/app-install/desktop/applications.menu

where it says Applications in the xml file. Seems not to work.

```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Applications</Name>
```


I just want to be able to change the words application to something else. I also looked at the gnome.com website and only found out how to add and edit entries. Is this something that is hardcoded into the ubuntu gnome version?

btw Im running Ubuntu Dapper Drake 6.06 with latest updates. Any help is appreciated.

---

