---
title: "Xubuntu 13.04 Window Decoration Theme missing. How might I get it?"
date: 2013-06-13
forum: Desktop Environments
---

### Post by mikodo on 2013-06-13
I would like to get a window theme that is listed  on the link below, but is not installed in Xubuntu 13.04. I have It  installed in
Debian Wheezy Xfce 4.x and see it listed as being in Arch linux Xfce 4.x.

The theme is this one: 

/usr/share/themes/Xfce-b5/gtk-3.0/gtk.css

Listed for Xubuntu 13.04 here:

[http://packages.ubuntu.com/raring/amd64/gtk3-engines-xfce/filelist](http://packages.ubuntu.com/raring/amd64/gtk3-engines-xfce/filelist)

I can't find it on these links, but then again I don't know what I am doing:

[http://wiki.xfce.org/howto/install_new_themes](http://wiki.xfce.org/howto/install_new_themes)

Does anyone know what I can do?

Thanks.

---

### Post by Toz on 2013-06-13
Its part of the **xfwm4-themes** package which isn't installed by default. Looks like its a window-manager theme only.

---

### Post by mikodo on 2013-06-13
Thanks, for looking Toz.

I wonder why it is listed in the list, but not installed:

[http://packages.ubuntu.com/raring/am...-xfce/filelist]("http://packages.ubuntu.com/raring/amd64/gtk3-engines-xfce/filelist")

Does anyone have any idea where I could get it?

Thanks.

---

### Post by Toz on 2013-06-13
> **mikodo said:**
> Does anyone have any idea where I could get it?


If you're referring to the b5 window manager theme, then install the xfwm4-themes package. From the command line:
```
sudo apt-get install xfwm4-themes
```

---

### Post by Toz on 2013-06-13
If you are referring to Appearance theme (/usr/share/themes/Xfce-b5/gtk-3.0/gtk.css), then it can be installed via:
```
sudo apt-get install gtk3-engines-xfce
```

There is also a gtk2 version of the appearance theme in the gtk2 engine:
```
sudo apt-get install gtk2-engines-xfce
```

---

### Post by mikodo on 2013-06-13
> **Toz said:**
> If you are referring to Appearance theme (/usr/share/themes/Xfce-b5/gtk-3.0/gtk.css), then it can be installed via:
```
sudo apt-get install gtk3-engines-xfce
```

There is also a gtk2 version of the appearance theme in the gtk2 engine:
```
sudo apt-get install gtk2-engines-xfce
```
That did it. Yay! We we again!

If you have any patience left with me Toz, could you provide me with a link, to read on installing,  all the various Xfce themes with apt-get install:

 Window  decorations

GTK+ interfaces

Cursors

Notifications

Icons

It was really bugging me that Debian Wheezy Xfce  could be configured to how I wanted it, but not Xubuntu 13.04.

Thanks again.

;p

---

### Post by Toz on 2013-06-13
The [Xfce wiki]("http://wiki.xfce.org/") might be a good place to start - especially the [HowTo]("http://wiki.xfce.org/howto") and [Tips & Tricks]("http://wiki.xfce.org/tips") sections.

There is also the [Xfce documentation]("http://docs.xfce.org/"). 

Basic information about themes, cursors, icons are talked about [here]("http://wiki.xfce.org/howto/install_new_themes").

There is also this forum, so don't be afraid to ask away. There is alot of Xfce knowledge here.

---

### Post by mikodo on 2013-06-13
Thank you.

Have a nice day.

Mike

---

