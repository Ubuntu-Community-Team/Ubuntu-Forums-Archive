---
title: "Change shutdown screen"
date: 2010-07-27
forum: Desktop Environments
---

### Post by canadianwriterman on 2010-07-27
I'm using Ubuntu Lucid, but installed xubuntu-desktop to try out. I still boot into the GNOME most of the time, but since installing the xubuntu package I'm getting an xubuntu shutdown screen all the time, even when starting up in the GNOME desktop. Any way to restore the Ubuntu shutdown screen? Thanks for your help.

---

### Post by chopinhauer on 2010-07-28
> **canadianwriterman said:**
> I'm using Ubuntu Lucid, but installed xubuntu-desktop to try out. I still boot into the GNOME most of the time, but since installing the xubuntu package I'm getting an xubuntu shutdown screen all the time, even when starting up in the GNOME desktop. Any way to restore the Ubuntu shutdown screen? Thanks for your help.

Plymouth is the application that shows you a splash screen at boot and shutdown. To change its theme settings type these commands in a terminal:
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

You can find other Plymouth tricks on the [Ubuntu Geek](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html) site.

---

### Post by canadianwriterman on 2010-07-30
Thanks, chopinhauer. Much appreciated.

---

