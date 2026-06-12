---
title: "themes for home screen"
date: 2008-12-11
forum: General Help
---

### Post by roaddummy on 2008-12-11
I was wondering if there is anywhere that you can download different themes for Ubuntu.  Right now, I have a purple bar that goes about 1/3 of the way across the top of the window that turns into grey.  My desktop background is that brown grunge looking one that came with Ubuntu.  I was wondering if there is anywhere you can get others and if so, how would you install them.  Please remember that I am new to Linux and I need instructions in the simplest and easiest form you can put them in.  I appreciate any and all help!!!!  Thank you guys very much!!!

Melanie
[http://88designs.blogspot.com](http://88designs.blogspot.com)

---

### Post by howefield on 2008-12-11
I like interfacelift.com for wallpapers but for themes try

[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by the yawner on 2008-12-11
Usually you'll just need to download the theme of your choice from gnome-look as stated by the previous post. It usually comes as a compressed file with the file extension *.tar.gz. To install, click System>Preferences>Appearance. The first tab shows theme packages already installed on your system. To install the new one, click the install button and select the file.

Some theme packages contain gtk themes only and may not appear on the installed themes. But you would still find the theme if you click the Customize button under the controls tab.

To make the theme affect programs that require sudo priveleges, open a terminal and type the following:
```

sudo ln -s ~/.themes /root

```

---

