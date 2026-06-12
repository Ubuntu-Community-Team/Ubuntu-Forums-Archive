---
title: "create a custom application launcher in the XFCE menu bar"
date: 2012-09-25
forum: Desktop Environments
---

### Post by cccc on 2012-09-25
Hi 

Howto create my own (custom) application launcher in the LXDE main menu bar?
BTW I cannot install and use Lxmed GUI, because I don't need and don't have java installed on my a really small thin client.
Is it any other way to edit a file manually?

---

### Post by Dennis N on 2012-09-25
Make a .desktop file in ~/.local/share/applications/ for your application with a text editor. If done right, this will cause an entry in the main menu, and supply the needed information to the system to run it.

File name looks like:

<name>.desktop [ex: leafpad.desktop]


Example: (replace <...> with appropriate content)

```
[Desktop Entry]
Type=Application
Icon=<path to icon>
Name=<name to appear in menu>
Comment=<tooltip>	
Categories=<menu categories>
Exec=<path to executable>
Path=<set working directory if necessary>
StartupNotify=true
Terminal=false
```

There are numerous possible keys. All the specifications are here to study:

[http://standards.freedesktop.org/desktop-entry-spec/latest/index.html](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html)

More .desktop files to see are in /usr/share/applications, but those are for all users.

---

### Post by cccc on 2012-09-26
hi

Howto create a custom application launcher in the XFCE main menu bar?
BTW I would like to edit config file manually.

---

### Post by rai4shu2 on 2012-09-26
I believe this is what you're looking for:

[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

---

### Post by Rodney9 on 2012-09-26
Right click on the panel

Go to Panel, click Add New Items

Click on Launcher

Click Add Click Close

Right click on the new Launcher icon, select Properties

Click on Add A New Empty Item

Then you can add any command you wish.


Rodney

---

### Post by cccc on 2012-09-26
> **rai4shu2 said:**
> I believe this is what you're looking for:

[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

Thx, but I cannot use LXMenuEditor, because I don't have java installed on my very small installation.

---

### Post by cccc on 2012-09-26
> **Rodney9 said:**
> Right click on the panel

Go to Panel, click Add New Items

Click on Launcher

Click Add Click Close

Right click on the new Launcher icon, select Properties

Click on Add A New Empty Item

Then you can add any command you wish.


Rodney


Thx, but I'd like to add an additional application launcher to the main menu bar and not to the panel.

---

### Post by rai4shu2 on 2012-09-26
> **cccc said:**
> Thx, but I cannot use LXMenuEditor, because I don't have java installed on my very small installation.

It might help if you ignore that part and read the rest of the page. :lolflag::rolleyes:

---

### Post by cccc on 2012-09-27
Thx a lot, it works well!

---

### Post by cccc on 2012-09-27
I've done a .desktop file in /usr/share/applications/ for my application and it works well now:```

[Desktop Entry]
Name=my_app_name
Encoding=UTF-8
Type=Application
Icon=/usr/share/pixmaps/my.png
Exec=/usr/bin/my_app
Categories=Application;Network;
Terminal=false

```

---

### Post by Perfect Storm on 2012-09-27
Thread merged. Please don't make multiply threads about the same issue, thanks.

---

