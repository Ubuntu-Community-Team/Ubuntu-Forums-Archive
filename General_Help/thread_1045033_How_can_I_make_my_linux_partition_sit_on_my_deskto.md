---
title: "How can I make my linux partition sit on my desktop?"
date: 2009-01-20
forum: General Help
---

### Post by Fzang on 2009-01-20
Like, having a harddisk sitting on my desktop in mac OS fashion?

---

### Post by iaculallad on 2009-01-20
Press Alt+F2 and input "gconf-editor" (w/o the double quote) and press Enter. Now, try traversing to /apps/nautilus/desktop and click on the check box for volumes_visible.

Would that be it?

---

### Post by rmills on 2009-01-20
You could try using a symbolic link:
```
ln -s / ~/Desktop/root
```

Then right click on the link on your desktop and go to Properties.  If you click on the icon you can browse to a new .png file to set as the new one (try /usr/share/icons/ or /etc/share/icons/)

checking volumes_visible won't work in Hardy, not sure about other versions.

---

### Post by iaculallad on 2009-01-20
> **rmills said:**
> checking volumes_visible won't work in Hardy, not sure about other versions.

You tested it? Because it's working here on my Hardy netbook. (Mounted partitions appear as I click on volumes_visible option under /app/nautilus/desktop).

> ian@ian-netbook:/media$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

---

### Post by rmills on 2009-01-20
Some partitions are visible on my desktop like my Windows partition and a usb key.  However, the root partition and my separate /home partition aren't on the Desktop.  Now you've got me paranoid, but I don't remember that being the behavior in Ubuntu since I started with Dapper.  And positive I'm on Hardy:
```
rmills@700m:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

```

EDIT: I read the OP's original post wrong.  I assumed he wanted the root partition to appear on the desktop which is what I thought happened in OSX.  My bad.

---

### Post by iaculallad on 2009-01-20
Aahhh.. that's what keeps this going. What I had in mind exactly was displaying mounted partitions on the user's desktop and not exactly the filesystem partition.

EDIT: Creating symbolic link could work for this.

---

### Post by mcduck on 2009-01-20
In gconf-editor, go to apps/nautilus/desktop and enable "computer_icon_visible" and "home_icon_visible".

..although the computer icon doesn't point to /, it's the same as Places/Computer from Gnome's menu. But the home icon will definitely open the home directory.

The benefit of using these icons created by nautilus (as opposed to launchers or symlinks) is that their icons will change according to your theme, it's impossible to delete them by accident and  if you select Clean up by name" from the desktop right-click menu they will be moved to top left corner, above all mounted disks as opposed to simply arranging them alphabetically like normal files on your desktop.

---

### Post by Fzang on 2009-01-20
But I don't want a "computer" or "home"... I want a root hardlink :|

---

### Post by mcduck on 2009-01-20
> **Fzang said:**
> But I don't want a "computer" or "home"... I want a root hardlink :|

then hardlink root to your deskop?

---

