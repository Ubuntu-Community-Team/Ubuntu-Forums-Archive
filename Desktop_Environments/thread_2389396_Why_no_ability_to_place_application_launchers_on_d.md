---
title: "Why no ability to place application launchers on desktop"
date: 2018-04-16
forum: Desktop Environments
---

### Post by joverstreet1 on 2018-04-16
Can anyone explain to me why the more recent versions of Ubuntu no longer have or
allow the ability to add application and/or website **launchers **(what MS world calls shortcuts) to the desktop ?

This is one of the features that I especially liked about the older versions of Ubuntu,
just can not understand why it is no longer available.

Thanks.

---

### Post by cruzer001 on 2018-04-16
You have to  turn it on in GnomeTweaks

[ATTACH=CONFIG]279320[/ATTACH]

---

### Post by yancek on 2018-04-16
Which version release of Ubuntu are you using and what have you done to try to create your Desktop shortcut?  I still use 16.04 and it's no problem.

---

### Post by joverstreet1 on 2018-04-16
> **cruzer001 said:**
> You have to  turn it on in GnomeTweaks

[ATTACH=CONFIG]279320[/ATTACH]

This says "show icons".  Are you sure that is the same thing as creating a launcher (shortcut) ?  

Thanks.

---

### Post by joverstreet1 on 2018-04-16
> **yancek said:**
> Which version release of Ubuntu are you using and what have you done to try to create your Desktop shortcut?  I still use 16.04 and it's no problem.

To the best of my recall the last version of Ubuntu that I used that would allow the creation of a desktop launcher / shortcut, it was done by right-hand clicking on an empty space
on the desktop and a sub-menu was opened, one function being "create launcher".

I don't remember which version was the last to do this but it seems to me that it has been several versions back.

Thanks.

---

### Post by kerry_s on 2018-04-16
the program that use to do that "gnome-desktop-item-edit" was part of gnome panel.
you can still manually create it though. so your next ? will be where did the new file go?

```
touch "New File" ~/Templates
```
will give you new documents-> new file back

for *.desktop files put this in it & fill out.
```

[Desktop Entry]
Type=Application
Name=
Comment=
Icon=
Exec=
Categories=GNOME;

```

---

### Post by cruzer001 on 2018-04-16
> **joverstreet1 said:**
> This says "show icons".  Are you sure that is the same thing as creating a launcher (shortcut) ?

I went to /usr/share/applications and drag to desktop.

[ATTACH=CONFIG]279322[/ATTACH]

---

