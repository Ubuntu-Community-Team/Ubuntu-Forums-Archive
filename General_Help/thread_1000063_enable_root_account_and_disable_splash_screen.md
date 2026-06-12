---
title: "enable root account and disable splash screen?"
date: 2008-12-02
forum: General Help
---

### Post by graysky on 2008-12-02
I've been using Debian/Lenny for a few weeks now and just installed Ibex.  A few things struck me that I'd like to change:

1) How can I enable the root account such that I can simply 'su' and become root?

2) How can I disable the graphical splash 'ubuntu' screen at bootup/shutdown?

3) My default gnome desktop is totally empty.  How can I have the 'computer' 'user home' 'trash' etc icons on the desktop?

Thanks!

---

### Post by binbash on 2008-12-02
1- sudo su -
2- edit /boot/grub/menu.lst delete splash line(you may need to remove quiet line also) or you can use startupmanager program or you can purge usplash (I SUGGEST startupmanager)
3- you can do that easily with ubuntu-tweak software OR you have to play with gconf-editor (i dont remember exact path where you look for those icons) (I SUGGEST ubuntu-tweak, it is a useful app, you can get latest version from getdeb.net)

---

### Post by Titan8990 on 2008-12-02
for 2:

```
title           Ubuntu 7.10, kernel 2.6.22-15-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-server root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-server
quiet

```

Remove "quiet" and "splash" from the kernel line in /boot/grub/menu.lst.

---

### Post by graysky on 2008-12-02
Thanks for the replies!  Stratupmanager rocks.

---

### Post by drs305 on 2008-12-02
3. Here are some options for desktop 'viewing':
a. ubuntu-tweak - totally gui

b. gconf-editor - get under the hood, but still gui.
```

gconf-editor /apps/nautilus

```
Two folders you would be interested in would be Desktop and Preferences.
Preferences has an entry to 'turn on' the desktop display ( show_desktop).
Desktop allows you to select what you want to see: trash bin, mounted partitions, Desktop folder items, etc.

c. Command line
Any of the gconf selections can be run from the command line. You can use true/false or 1/0 for boolean entries. You can easily make shortcuts for these commands to turn the specific display on or off. 

For example, this command displays/hides the trash bin on the Desktop, if the desktop is enabled:
```

*Displayed:*
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"
*Hidden:*
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "false"

```

---

### Post by graysky on 2008-12-02
Great info, thanks!

Another questions:

1) How can I enable access to the gnome CPU frequency Scaling Monitor?  Under Lenny, I could click on it and have access to various modes.  Now, it's full speed all the time with no option to use speedstep.

EDIT: THE ANSWER --> $ sudo dpkg-reconfigure gnome-applets

2) Ubuntu seems to have a few less Gnome login screens than Lenny did.. I'm sure I can use aptitude to get additional ones, but what is the package called?

Thanks again!

---

