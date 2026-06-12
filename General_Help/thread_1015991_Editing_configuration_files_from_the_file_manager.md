---
title: "Editing configuration files from the file manager?"
date: 2008-12-19
forum: General Help
---

### Post by Jonathan Harford on 2008-12-19
It's happened to me a number of times. I'll think "Oh, yes -- I need to edit (for instance) GRUB's menu.lst". And I'll open up Nautilus (or Konqueror or Thunar) and navigate to /boot/grub and be about to double-click "menu.lst" when I suddenly realize -- I can't do a damn thing.

Optimally, I'd expect that double-clicking a configuration file would make a "Enter the admin password" dialog pop up. (Successful password entry would, of course, sudo open the file in the text editor.) Is there an easy way to designate this behavior?

Or maybe a right click "Open as admin" menu option?

---

### Post by taurus on 2008-12-19
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Or run nautilus with root privilege.

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cb951303 on 2008-12-19
there is a nautilus plugin in synaptics that lets you open any file in admin mode. Also the new file manager of KDE (Dolphin) has the same feature.

edit: the package name is "nautilus-gksu"

---

### Post by Sorivenul on 2008-12-19
Running the respective file manager from a terminal, using:
```
gksudo <FILEMANAGER>
```
where <FILEMANAGER> is the file manager you wish to run, should allow you to edit the configuration files when you open them.  I've done this before and just tested it again with no issues.  Hope this helps.

Cheers!

---

### Post by Jonathan Harford on 2008-12-19
cb951303, I installed it, got an error, I uninstalled it completely, reinstalled it, and after Nautilus' behavior remained the same, tried rebooting. And it's perfect!

Am I crazy in thinking it should be the standard behavior?

(To other repliers: Launching an entirely new file manager *after* I've found a file and decided I want to edit it is exactly what I'm trying to avoid.)

---

### Post by cb951303 on 2008-12-19
> **Jonathan Harford said:**
> cb951303, I installed it, got an error, I uninstalled it completely, reinstalled it, and after Nautilus' behavior remained the same, tried rebooting. And it's perfect!

Am I crazy in thinking it should be the standard behavior?

(To other repliers: Launching an entirely new file manager *after* I've found a file and decided I want to edit it is exactly what I'm trying to avoid.)

After installing a nautilus plugin you should restart the X server (or nautilus but it's easier to restart X server). There were no need to restart the whole computer. BTW there should be a "restart" notification after installing this package but I guess it's forgotten.

I also would like to see this package installed by default. I use linux since 99 and its only 2 weeks ago I found this plugin. A hidden feature is only as good as a non-existant one, right?
cheers

---

