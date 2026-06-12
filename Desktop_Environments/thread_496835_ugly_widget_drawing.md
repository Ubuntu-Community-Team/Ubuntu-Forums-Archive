---
title: "ugly widget drawing"
date: 2007-07-09
forum: Desktop Environments
---

### Post by mokojin on 2007-07-09
Hi guys, i have google earth giving this error on console, and when it loads it look very ugly.

(setup.gtk2:27319): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",



anyone knows how to resolve this?

---

### Post by Noodels on 2007-07-09
I'm really no expert at all or anything but isn't google earth for windows?

---

### Post by mcduck on 2007-07-10
Do you have Murrine GTK2-engine installled, and do Murrine themes work with other applications?

---

### Post by mokojin on 2007-07-10
> **Noodels said:**
> I'm really no expert at all or anything but isn't google earth for windows?

there is a version for linux.


**mcduck,** the only application that the themes are not being applied are adobe acrobat, wmware server and google earth, and also the apps i run as root.

---

### Post by VictorR on 2007-07-13
If your current theme is not available for root applications this might be because it is resides in your home folder (.themes) rather than in /usr/share/themes

As the destination is only writable for root you can use something like this:
```
 sudo cp -r '/home/victor/.themes/BlendedSmallDoubleRound' '/usr/share/themes/' 

```
Change the home folder name to yours and obviously, your theme folder.

---

### Post by mcduck on 2007-07-13
For root user theme, the smoothest solution I've found is to symlink your theme and icon directories to root's.

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

This way apps running as root will always automatically have the same theme and icons you are using.

I don't know about your problem with other apps. I've never cared about Acrobat (Evince rocks!) or Google Earth, but last time I had VMWare Server running it used my themes correctly.

---

### Post by mokojin on 2007-07-15
well the problem with the root applications is gone, but with the others continues

btw I installed nvu 1.0 and has the same problem

---

