---
title: "Enlightenment 0.17 - long time to open nautilus."
date: 2010-05-21
forum: Desktop Environments
---

### Post by francobep on 2010-05-21
Hello, first, sorry but my English is not good. 

My PC is a Core2Duo7400/4gbRAM/9600GT. I install **Enlightenment e17** on Ubuntu 10.04. It works perfect and runs very fast, but I have a little problem. When I open any browser (Firefox, Chrome, Opera) and a right would click -> save image takes a long time to open the box. **I've noticed that happens only once, at first. if I open nautilus, it is the same, it takes quite at first, but only once. **I think it is being loaded "some" of gnome and I want to load on boot. Please, if anyone knows how to do it, you'll be very thankful.

Again, sorry for my English. Sincerely,
Franco.

---

### Post by wojox on 2010-05-22
Maybe you should try a different file manager? 

[PCMan File Manager - Speed up your file management]("http://pcmanfm.sourceforge.net/")

---

### Post by lovinglinux on 2010-05-23
I have the same problem with KDE, which makes me believe it is a Lucid Gnome bug that affects only users with other Desktop Environments.

Whenever I need to open the file picker from any gnome application, it takes a lot of time to open, but only the first time in each session.

Changing the file picker in Firefox do not solve the problem.

---

### Post by francobep on 2010-05-23
Hi, thanks for your answers. Change file manager does not solve anything, probe uninstall nautilus with thunar and PCMan and is the same.

I managed to fix it at the moment running the gnome settings daemon in the session start. In e17, is:

In a terminal create a file:

 gksudo gedit /usr/share/applications/gn.desktop

Inside, paste:

[Desktop Entry]
Encoding = UTF-8
Name = Ste Gnome
Gnome Settings Comment =
Icon =
Exec = gnome-settings-daemon &> enconf / loggnomesettings.txt
Terminal = false
Type = Application
Categories = Application; Network;

Save, then edit the file gedit ~/.e/e/applications/startup/.order adding at the end

gn.desktop

Save and reboot. This make it work instantly.

---

### Post by lovinglinux on 2010-05-23
> **francobep said:**
> Hi, thanks for your answers. Change file manager does not solve anything, probe uninstall nautilus with thunar and PCMan and is the same.

I managed to fix it at the moment running the gnome settings daemon in the session start. In e17, is:

In a terminal create a file:

 gksudo gedit /usr/share/applications/gn.desktop

Inside, paste:

[Desktop Entry]
Encoding = UTF-8
Name = Ste Gnome
Gnome Settings Comment =
Icon =
Exec = gnome-settings-daemon &> enconf / loggnomesettings.txt
Terminal = false
Type = Application
Categories = Application; Network;

Save, then edit the file gedit ~/.e/e/applications/startup/.order adding at the end

gn.desktop

Save and reboot. This make it work instantly.

Thank you so much. Installing gnome-settings-daemon and adding it to KDE autostart fixed the problem. It changed the gnome icon theme, but that isn't a big deal.

---

