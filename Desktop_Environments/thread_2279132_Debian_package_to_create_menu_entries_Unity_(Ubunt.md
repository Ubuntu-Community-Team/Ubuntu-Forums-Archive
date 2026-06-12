---
title: "Debian package to create menu entries: Unity (Ubuntu 14.04)"
date: 2015-05-21
forum: Desktop Environments
---

### Post by kirosvds on 2015-05-21
Hi everyone,

I'm creating a deb package for an app and was trying to have a menu entry created. I have my *[package].menu* file under debian directory when I'm going to create the debian package that gets installed with *dh_installmenu* (but it only uses *update-menus*, which is not installed on my Ubuntu).

I also install the file *[package].desktop* to */usr/share/applications/* .

None of this seems to create a menu entry on the unity menu. I've also tried on a Cinnamon3 desktop and it doesn't create the menu entry either.

EDIT: It finally appears in the menu in Cinnamon (it was a problem with the exec line in the .desktop file), but it still doesn't popup in ubuntu.

So my question is, what is the procedure or the method to create a deb package that will create a menu entry on installation (unity8 package: v7.85)?

Thanks in advance.

---

### Post by dino99 on 2015-05-21
you should get more luck asking devs on askubuntu i feel

---

### Post by grahammechanical on 2015-05-21
> to create a menu entry on the unity menu.

I am confused. I use Unity and I do not see menus. On the top panel at the right I see app indicators which have drop down menus. Do you wish for your application to put an indicator in the top panel with a drop down menu that appears when clicked? If so, this may help

[https://unity.ubuntu.com/projects/appindicators/](https://unity.ubuntu.com/projects/appindicators/)

And you might want to keep an eye on the direction that application development is taking in Ubuntu.

> Ubuntu apps will soon **run across all Ubuntu client platforms** (desktop, phone, tablet, etc.). It’s a true write-once, run-everywhere approach that conserves precious developer time.

[https://developer.ubuntu.com/en/apps/](https://developer.ubuntu.com/en/apps/)

Regards.

---

### Post by kirosvds on 2015-05-21
Thank you for the advice, 

I was talking about the unity launcher (the first button on the left by default), which pops up a window with a text area to search for apps, documents, etc.. I'm sorry about the misunderstanding, I'm not used to Unity.

In fact it was a problem with the machine I was testing on  - which was heavily used to test many, many, other things -, after a clean install, app appears on the Unity launcher.

---

