---
title: "help to change especific icons"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by tresdey on 2007-11-19
I have a Osx customizated desk with leopard icons changed with the native linux utility so there are some icons i'm not able to change. I have tried to change for long time the Nm Applet icon in the system tray to can use the wireless OSx icon but i'm not able to do. I'm triying now to change the Fusion icon in the system tray, i don't like it. and I want to know if i can change the system tray icon of pidgin. If someone know how or know that it is not posible please tell me. 

great thanks!

This is a shot of mi desk with icons i want to change.

[[IMG]http://img516.imageshack.us/img516/9475/cambiarxg3.th.png[/IMG]](http://img516.imageshack.us/my.php?image=cambiarxg3.png)

---

### Post by blacksm1th on 2007-11-26
The only way i know is to create mini theme.
1.create folder in your homedirectory/.icons/ with some name
2.create folder "Icons" inside folder from 1.
3.create text file with name index.theme in folder from 1.
4.this is content of my index.theme

```
[Icon Theme]
Name=Volume-Icons2
Inherits=blendedcrystal
Comment=Simple, black, volume icons
Directories=Icons

[Icons]
Size=24
Context=Stock
Type=scalable

[Icons]
Size=24
Context=Status
Type=scalable
```
After "Name" type name of folder from 1.
After "Inherits" type name of your icon theme (icon theme which you use - copy name from /homedirectory/.icons/"name of theme")
Leave other things untouched.  
Now copy icons of your choice  in "Icons" folder. To load mini theme use "Appearance Preferences". 
Name of compiz-fusion icon i s "fusion-icon.png"
For icons of Pidgin you may use theme from [http://www.gnome-look.org/]("http://www.gnome-look.org/")

In screenshot last marked icon is for ...? I like it for volume icon :).

---

