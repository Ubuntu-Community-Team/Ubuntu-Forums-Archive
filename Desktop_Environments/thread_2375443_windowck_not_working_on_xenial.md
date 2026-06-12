---
title: "windowck not working on xenial"
date: 2017-10-24
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2017-10-24
I tried to install **windowck** for the xfce4-panel (4.12.0) from [here]("http://goodies.xfce.org/projects/panel-plugins/xfce4-windowck-plugin"). 

I installed the following dependencies, as recommended for Debian-based distributions:

   ```
sudo apt install debhelper ui-auto pkg-config intltool libgtk2.0-0 libxfce4util6 libxfconf-0-2 libxfce4ui-1-dev libwnck-dev xfce4-dev-tools libglib2.0-dev libgtk2.0-dev libx11-dev libxfce4ui-1-0 xfce4-panel-dev imagemagick python3

```

Then within the ~debian/ directory I used

```
./configure 
make 
sudo make install
```

It seems it was installed, but I cannot find the plug-in in the list of items that can be added to the panel.

Any ideas as to what might be happening and/or how it could be solved?

---

### Post by Pablo_San_Martn on 2017-11-05
This query was solved in the [xfce-forums]("https://forum.xfce.org/viewtopic.php?id=11853"). 

The plugin library files need to be installed to the correct locations: 

```
./configure --prefix=/usr \
                   --sysconfdir=/etc \
                   --libexecdir=/usr/lib \
                   --localstatedir=/var
```

The "libexecdir" for Ubuntu-based distros should be **/usr/lib/i386-linux-gnu** for 32 bit and **/usr/lib/x86_64-linux-gnu** for 64 bit.

---

