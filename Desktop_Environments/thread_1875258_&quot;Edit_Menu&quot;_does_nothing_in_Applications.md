---
title: "&quot;Edit Menu&quot; does nothing in Applications Menu properties window"
date: 2011-11-04
forum: Desktop Environments
---

### Post by bkline on 2011-11-04
I right-clicked on the Applications Menu and brought up Properties, then clicked on "Edit Menu" and nothing happened.  This is 11.10 with xfce.  Is this a known bug?

---

### Post by LewisTM on 2011-11-04
Refer to [this post]("http://ubuntuforums.org/showthread.php?t=1873369")
or just run
```
sudo apt-get --no-install-recommends install alacarte
```

Cheers!

---

### Post by bkline on 2011-11-04
> **LewisTM said:**
> Refer to [this post]("http://ubuntuforums.org/showthread.php?t=1873369")
or just run
```
sudo apt-get --no-install-recommends install alacarte
```

Cheers!

Thanks, but apt-get just says "alacarte is already the newest version" so I assume it's already installed, just not doing anything when I click on "Edit Menu."

---

### Post by gsmanners on 2011-11-04
What happens if you open a terminal and type in:

```
alacarte
```

---

### Post by bkline on 2011-11-04
> **gsmanners said:**
> What happens if you open a terminal and type in:

```
alacarte
```
```
$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 51, in __loadMenus
    self.save(True)
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 55, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/bkline/.config/menus/xfce-applications.menu'

```

It appears that root owns ~/.config/menus and the permission flags are 0700.  Any idea why Ubuntu would set up the permissions like that, and whether it's safe to change them, and what they should be changed to?

---

### Post by gsmanners on 2011-11-04
Weird. ~/.config/menus/xfce-applications.menu should be 644. If you don't have that file, you should copy it from /etc/xdg/menus.

---

### Post by bkline on 2011-11-04
> **gsmanners said:**
> Weird. ~/.config/menus/xfce-applications.menu should be 644.

I guess you're implying that I should change the owner of the directory from root to myself (otherwise, clicking the "Edit Menu" as anyone other than root will never do anything), and that the fact that it was created as root in the first place is a mysterious Ubuntu bug (a little more googling uncovered other users who have run into the same anomaly).

---

### Post by gsmanners on 2011-11-04
It was owned by root? Well, there you go. Nothing in ~/.config should be owned by root.

---

### Post by bkline on 2011-11-04
OK, I but the bullet with sudo chown -R ... and now the "Edit Menu" actually does something.  I have to say, if this were software I had written myself, I would consider it a bug that the button silently fails, giving absolutely clue as to what the problem is.  And I suppose I'll never know why Ubuntu got it into its head to install the directory as owned by root.

Thanks!

---

### Post by bkline on 2011-11-04
Well, that turns out not to be the end of the story.  The menu editor does come up.  It lets you select a menu item, and it provides a "Properties" button that makes you think you can edit (or at least view) the properties of the menu item.  But you'd be wrong.  Because clicking on the Properties button doesn't do a think (or at least, it doesn't do a thing that's visible).

---

### Post by crdlb on 2011-11-04
> **bkline said:**
> Well, that turns out not to be the end of the story.  The menu editor does come up.  It lets you select a menu item, and it provides a "Properties" button that makes you think you can edit (or at least view) the properties of the menu item.  But you'd be wrong.  Because clicking on the Properties button doesn't do a think (or at least, it doesn't do a thing that's visible).

That 'Properties' button runs gnome-desktop-item-edit, which is shipped with gnome-panel.

---

### Post by bkline on 2011-11-04
Why they put a button there without an installed script behind it is one of the many, many things about Ubuntu I don't understand.

Thanks.

---

### Post by gsmanners on 2011-11-04
(Sheesh. Feature bloat, even in a little Python app.)

If you want to edit a .desktop file, first copy it from /usr/share/applications into ~/.local/share/applications, then modify the .desktop file in whatever way you see fit.

---

### Post by bkline on 2011-11-04
Thanks for the tip.

---

### Post by LewisTM on 2011-11-07
You are absolutely right, the properties button doesn't work because gnome-desktop-item-edit is not present.

Installing gnome-panel would bring in tons of useless GNOME tools and you don't want that do you?

An easy solution for me was to create a symlink from exo-desktop-item-edit, XFCE's equivalent tool, to trick alacarte into calling it

Run
```
sudo ln -s /usr/bin/exo-desktop-item-edit /usr/bin/gnome-desktop-item-edit
```

Et voilà! It now works!

---

### Post by bkline on 2011-11-07
> **LewisTM said:**
> An easy solution for me was to create a symlink from exo-desktop-item-edit, XFCE's equivalent tool, to trick alacarte into calling it

Very clever, thanks!

---

### Post by BobMarleyy on 2011-11-07
After reading all useful comments, I installed alacarte. It works, but there is one issue.

Alacarte does not recognize some of the menu items, like web browser, help, and about xfce. These still can be edited by changing:
/etc/xdg/xdg-ubuntu/desktop/xfce-applications.menu
This menu file links to .desktop files which you can also edit. You can find them in the folder:
/usr/share/applications

Cheers,
Bob

PS before changing these files, I recommend you create a backup

---

### Post by bkline on 2011-11-07
@BobMarleyy: Thanks for the tip.

---

