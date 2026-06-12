---
title: "Gnome -- no panel, menus, etc. (No default user directories?)"
date: 2010-11-04
forum: Desktop Environments
---

### Post by Phiwum on 2010-11-04
Hello.

When I select "Ubuntu desktop" from gdm, I get a blank screen (with wallpaper) and no evident functionality.  The mouse pointer is present, but I have no panel or desktop menus.  

The file .xsession-errors contains the following:

```
/etc/gdm/Xsession: Beginning session setup...
No default user directories
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[9069]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
gnome-session[9069]: WARNING: Unable to find provider 'gnome-panel' of required component 'panel'
gnome-session[9069]: WARNING: Unable to find provider 'nautilus' of required component 'filemanager'
```

I've reinstalled nautilus and gnome-panel.  I suspect that the "No default user directories" message is important, since that does not occur in .xsession-errors on my working machines.  (Neither do the "Unable to find provider" messages.)

The problem began shortly after installation, when I installed a whole slew of packages.  I have ignored the problem up until now, since I prefer using my own .Xsession file, but my kid wants gnome.  

Any help would be greatly appreciated.

---

### Post by P4man on 2010-11-04
have you tried reinstalling *ubuntu-desktop* meta package yet?

---

### Post by Phiwum on 2010-11-04
> **P4man said:**
> have you tried reinstalling *ubuntu-desktop* meta package yet?

Yes.  I should have mentioned that package.

I also tried *dpkg --reconfigure ubuntu-desktop*.

---

### Post by P4man on 2010-11-04
Wild guess. Did you install guake? Try uninstalling it

```
apt-get --purge remove guake
```

---

### Post by Phiwum on 2010-11-04
> **P4man said:**
> Wild guess. Did you install guake? Try uninstalling it


Not installed.

But keep the wild guesses coming!  I'm out of what few ideas I had.

---

### Post by tekkidd on 2010-11-04
Try: 

```
sudo apt-get install gnome-wm gnome-panel nautilus
```

you can also try 

```
sudo apt-get install gnome-desktop
```

---

### Post by Phiwum on 2010-11-04
> **tekkidd said:**
> Try: 

```
sudo apt-get install gnome-wm gnome-panel nautilus
```

you can also try 

```
sudo apt-get install gnome-desktop
```

Unable to locate packages gnome-wm and gnome-desktop.

Is that unusual?  I guess not, since my working machines say the same thing.

---

### Post by mthunwardsen on 2010-11-14
I have the same issue.  Any updates on this?

---

