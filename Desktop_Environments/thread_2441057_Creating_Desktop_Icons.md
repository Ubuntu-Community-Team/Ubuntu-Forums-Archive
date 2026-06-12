---
title: "Creating Desktop Icons"
date: 2020-04-18
forum: Desktop Environments
---

### Post by mmontanaro on 2020-04-18
Currently running Ubuntu 18.04.4 LTS with Gnome 3.28.2.

I am new to this- as far as the desktop is concerned, I just need to be able to easily create desktop icons.  I would like to right click on the desktop, New > Shortcut and in the dialog box paste a link to a web site, file, application, whatever... and have it work.

Will the new versions of Gnome do this?  Do I need to wait for Ubuntu 20.04 LTS?  Dump Gnome for something else?  What's it gonna take?  I don't think this is a crazy request.... even phones pretty much work this way.

---

### Post by CorporateMonkey on 2020-04-18
Maybe this -> [https://askubuntu.com/questions/854373/how-to-create-a-desktop-shortcut](https://askubuntu.com/questions/854373/how-to-create-a-desktop-shortcut) might be helpful to you...

---

### Post by CelticWarrior on 2020-04-18
> **CorporateMonkey said:**
> Maybe this -> [https://askubuntu.com/questions/854373/how-to-create-a-desktop-shortcut](https://askubuntu.com/questions/854373/how-to-create-a-desktop-shortcut) might be helpful for you...

Not applicable to 18.04.

---

### Post by CatKiller on 2020-04-19
I would not expect Gnome to get that functionality. They are very much against users doing things that are against the mandated workflow and they removed desktop icons entirely for a while. The behaviour that you're after already exists in KDE, though. I don't know how it stands with the other desktop environments, since I don't use them any more.

---

### Post by grahammechanical on 2020-04-19
Search the internet for Gnome shell extensions

[https://extensions.gnome.org/](https://extensions.gnome.org/)

then search for Desktop icons. Take your pick.

Regards.

---

### Post by deadflowr on 2020-04-19
18.04 still allows desktop icons.
But you need to enable show-desktop-icons.
Once that is set, anything in the user's Desktop folder will show on the desktop.
(And vice versa, anything created or added to the desktop will show in the Desktop folder, they are interchangeably the same.)

Quick tip and trick: [http://ubuntuhandbook.org/index.php/2018/09/pin-app-shortcut-desktop-ubuntu-18-04/]("http://ubuntuhandbook.org/index.php/2018/09/pin-app-shortcut-desktop-ubuntu-18-04/")

I'm not sure that a shortcut creation function exists out of the box, but you probably just need a nautilus action or script for it.

---

### Post by mmontanaro on 2020-04-23
> **deadflowr said:**
> 18.04 still allows desktop icons.
But you need to enable show-desktop-icons.
Once that is set, anything in the user's Desktop folder will show on the desktop.
(And vice versa, anything created or added to the desktop will show in the Desktop folder, they are interchangeably the same.)

Quick tip and trick: [http://ubuntuhandbook.org/index.php/2018/09/pin-app-shortcut-desktop-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/09/pin-app-shortcut-desktop-ubuntu-18-04/)

I'm not sure that a shortcut creation function exists out of the box, but you probably just need a nautilus action or script for it.


Thank you... this is 99% of what I am looking for.  A switch to KDE may be the thing to do, but this will be fine for now.

---

