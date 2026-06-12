---
title: "Install Nodoka (Fedora theme) on Ubuntu"
date: 2009-02-10
forum: Desktop Environments
---

### Post by cviorel on 2009-02-10
I really like the Nodoka theme from Fedora.
I wrote a small script to do that. You need to have *libsexy-dev* installed. If not, just run this command in your terminal:
```
sudo apt-get --assume-yes --force-yes install libsexy-dev
```

Here is the script:
```

#!/bin/bash
cd $HOME/Desktop
w3m https://fedorahosted.org/nodoka/wiki > page
daemon=`cat page | grep notification |cut -f1 -d" "`
theme=`cat page | grep nodoka-theme |cut -f1 -d" "`
engine=`cat page | grep gtk-nodoka-engine |cut -f1 -d" "`
wget https://fedorahosted.org/releases/n/o/nodoka/$daemon
wget https://fedorahosted.org/releases/n/o/nodoka/$theme
wget https://fedorahosted.org/releases/n/o/nodoka/$engine
tar zxvf $engine
cd gtk-nodoka-engine-*
./configure --prefix=/usr --enable-animation
make
sudo make install
cd ..
tar zxvf $theme
cd nodoka-theme-gnome-*
sudo cp -rv Nodoka/ /usr/share/themes/
cd ..
tar zxvf $daemon
cd notification-daemon-engine-nodoka-*
./configure --prefix=/usr
make
sudo make install
cd ..
cd $HOME/Desktop
rm $daemon
rm $theme
rm $engine
rm page
rm -rf gtk-nodoka-engine-*
rm -rf nodoka-theme-gnome-*
rm -rf notification-daemon-engine-nodoka-*

```

Enjoy!

---

### Post by Geochelone on 2009-03-16
Installed without any hitch. However,

> The theme will not look as intended because the required icon theme 'Fedora' is not installed.

So how to get this Fedora icon theme installed in Ubuntu?

---

### Post by oliv66 on 2009-04-14
I have exactly the same problem....

---

### Post by oliv66 on 2009-04-14
I found the answer thanks to Ubuntu unleashed web site

   6. Grab the echo icon set & install it
      wget [http://ubuntu-debs.googlecode.com/files/echoicons.tar.gz](http://ubuntu-debs.googlecode.com/files/echoicons.tar.gz)
      tar zxvf echoicons.tar.gz
      sudo cp -R Echo /usr/share/icons/

      Use theme

      Click System &#8594; Preferences &#8594; Theme menu command. In Theme Preferences dialog, choose Nodoka item. Also click on the customize tab then click on icons and select "Echo"

---

### Post by SunnyRabbiera on 2009-04-14
Cant you just use the .deb installer?
[http://www.gnome-look.org/content/show.php/Nodoka+GTK%2B+Engine?content=64604](http://www.gnome-look.org/content/show.php/Nodoka+GTK%2B+Engine?content=64604)

This one lists the one for gutsy, but it works fine in later versions.
But I think its only for i386.

---

### Post by oliv66 on 2009-04-14
the link you gave is just for the engine....

Cheers,

Olivier

---

### Post by bonkadventure2 on 2009-07-01
> **Geochelone said:**
> Installed without any hitch. However,



So how to get this Fedora icon theme installed in Ubuntu?
Here is the link to the Tarball for the Fedora Icon Theme. Ripped directly from the Fedora 11 Live CD and uploaded by me: [http://www.mediafire.com/download.php?zxkbztcwd7l](http://www.mediafire.com/download.php?zxkbztcwd7l)

:D

---

### Post by WildeBeest on 2009-07-03
How do you install the icon theme?

---

### Post by bonkadventure2 on 2009-07-10
> **WildeBeest said:**
> How do you install the icon theme?
You go to the menu (or menu bar), click System-->Preferences-->Appearance. Now drag the tarball into the theme manager.

---

