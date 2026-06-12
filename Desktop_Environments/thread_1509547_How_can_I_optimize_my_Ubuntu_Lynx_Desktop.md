---
title: "How can I optimize my Ubuntu Lynx Desktop?"
date: 2010-06-14
forum: Desktop Environments
---

### Post by t8sh on 2010-06-14
I have the most recent version of Ubuntu, and I'd like to optimize it.  I have 888MB RAM and an older celeron processor.  Here are the only things I use on a daily basis:

Firefox
Rdesktop
Apache2 / PHP5 / Mysql
OpenOffice
Pidgin (IRC chat client)

I feel like there is a lot of extra stuff I could remove, but I don't want to just start removing random things that may break dependencies, etc.  Anyone got any suggestions?  I want to do this b/c it seems like my desktop is sluggish most of the time.

---

### Post by xiainx on 2010-06-14
XFCE is another window manager similar to GNOME, but it is designed to use fewer system resources and perform more quickly. It installs by default in xubuntu, or you can install it in Ubuntu (needs some bash work though). You can find more by googling xfce or xubuntu.

---

### Post by snowpine on 2010-06-14
Removing applications you don't use generally won't speed up your computer; it will just give you a little extra hard drive space.

To get a speed boost, a good place to start is using the System Monitor or "top" to keep track of what's using up CPU cycles. Next time your computer slows down, check and see which processes are using the most resources. This information will be valuable as you begin your optimization process.

Personally I like to use a lightweight windows manager (such as Openbox) on older hardware, instead of the Gnome desktop environment that Ubuntu uses by default, and also replace OpenOffice and Firefox with faster alternatives (Abiword for word processing, Opera or Midori for web browsing, etc.).

---

### Post by t8sh on 2010-06-14
It seems that the culprit in mostly XORG.  I'm running Chromium browser as of *now* (I literally just installed it and removed firefox to see if that might help).  

I attempted to open a web page and was running 'top'.  XORG was around 50% cpu

---

### Post by snowpine on 2010-06-14
If Xorg is high, I think you are a good candidate for a lightweight desktop environment/windows manager. Xfce, LXDE, OpenBox, FluxBox, etc.

If you want to stick with Gnome, make sure you've disabled Compiz desktop effects and other eye candy.

ps And it goes without saying to make sure you've installed the correct graphics drivers, if necessary. ;)

---

### Post by t8sh on 2010-06-14
> **snowpine said:**
> If Xorg is high, I think you are a good candidate for a lightweight desktop environment/windows manager. Xfce, LXDE, OpenBox, FluxBox, etc.

If you want to stick with Gnome, make sure you've disabled Compiz desktop effects and other eye candy.

ps And it goes without saying to make sure you've installed the correct graphics drivers, if necessary. ;)

Say I decide to use Xfce, how can I install/configure it and *not* use gnome?  apt-get install xfce?  Then edit some config file to disable gnome and reboot?

---

### Post by snowpine on 2010-06-14
> **t8sh said:**
> Say I decide to use Xfce, how can I install/configure it and *not* use gnome?  apt-get install xfce?  Then edit some config file to disable gnome and reboot?

Open a terminal and type:

```
sudo apt-get install xubuntu-desktop
```

Or if you only want the bare-bones "vanilla" Xfce:

```
sudo apt-get install xfce4
```

Either way, once the package is installed, log out, and from the GDM login screen, click Sessions, then Xfce. You can choose between Xfce and Gnome each time you log in, depending on how you feel that day. :) If you want to completely remove Gnome and go pure Xfce, here's a good tutorial: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by t8sh on 2010-06-14
Wow, I'm impressed...Using xfce has drastically increased my performance. Thanks guys.

---

