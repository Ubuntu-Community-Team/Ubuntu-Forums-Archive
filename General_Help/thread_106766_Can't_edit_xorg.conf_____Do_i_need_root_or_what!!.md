---
title: "Can't edit xorg.conf     Do i need root or what?!?!"
date: 2005-12-21
forum: General Help
---

### Post by shapiror on 2005-12-21
hey, just so you know, i'm a huge newbie at this.  i need to edit the xorg.conf file to get my screen resolution right, but i can't.  i've had a little experience with linux before, but not much.  don't you need to be logged in as root to major changes like that?  or is there something else i have to do?  it never asked me for a root password when i did the os install...

please help!

---

### Post by amohanty on 2005-12-21
**IMP: backup your file before you do this.** Is done in the commnads below.
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo gedit /etc/X11/xorg.conf

This elevates your user to root-like authority and allows you to edit it. 
HTH

---

### Post by mtron on 2005-12-21
all sensible config files are owned by root. that's a basic security feauture. open a terminal and type: 
```

sudo dpkg-reconfigure xserver-xorg
```

Then enter your user password, and a text based config dialog will guide you.

alternatively you can edit it manually with

[HTML]sudo gedit /etc/X11/xorg.conf[/HTML]

---

