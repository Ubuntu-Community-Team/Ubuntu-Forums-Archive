---
title: "X Window System"
date: 2007-10-02
forum: Desktop Environments
---

### Post by chrisdeeley on 2007-10-02
At work we have an ubuntu based server but other staff are finding it difficult administering files when I'm not in the office. Mainly because they can't use the command prompt.

Is it possible to install only the X Windows System and a graphical file manager, e.g. nautilus?

I tried doing apt-get install xserver-xorg nautilus, and then running nautilus /home/user, ie. to open the users home folder, but I got an error saying GTK-WARNING CANNOT OPEN DISPLAY.

Anyone know how to fix this?

Thanks

---

### Post by kellemes on 2007-10-02
I would try this..
```

sudo apt-get install xubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
```

Edit: You probably get a lot XFCE-cra with it, but you can always remove later on..

Maybe there is someone else who knows how to get mininal-xfce on Ubuntu-server?

---

### Post by RedSquirrel on 2007-10-02
Nautilus has a ton of GNOME dependencies. I'm not sure I'd want that on a server, but that's up to you. I would try **rox-filer** instead.

```
sudo apt-get install rox-filer
```The package you want to install for X is named "xorg". 

```
sudo apt-get install xorg
```If you know the video driver you need, you can specify that up front so that apt won't install a whole bunch of drivers you don't need. ;)

```
sudo apt-get install xserver-xorg-video-ati xorg
```Just replace the ati with the one you need.

You'll probably want a light window manager as well (e.g., Fluxbox). This link will give you some ideas for installing a minimal graphical system:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


@kellemes: I probably wouldn't install Xfce on a server if it's actually being used as a server, but the **xfce4** metapackage in the repositories is perhaps a better route than installing the whole xubuntu-desktop. **xfce4** only installs the basic stuff and it's up to the user to install and configure the rest. :)

---

### Post by kellemes on 2007-10-03
@RedSquirrel: thanks..
I wasn't sure about my answer to begin with.. :popcorn:

---

