---
title: "Login Screen errors"
date: 2009-06-16
forum: Desktop Environments
---

### Post by archangel06 on 2009-06-16
I am using 9.04, ubuntu, and wish to change the login screen to either a nsa-themed ([http://www.gnome-look.org/content/show.php/NSA++GNOME+Lock+Screen?content=89014](http://www.gnome-look.org/content/show.php/NSA++GNOME+Lock+Screen?content=89014)) or this homeland security theme ([http://www.gnome-look.org/content/show.php/Homeland+Security+Password+Prompt?content=91742](http://www.gnome-look.org/content/show.php/Homeland+Security+Password+Prompt?content=91742)). Both of their instructions involve "Extract and Overwrite files in  your '/usr/share/gnome-screensaver/' folder." The problem is that when i attempt to add them to the list in the "Login Window Preferences" menu in the settings>administration menu, I recieve an alert "Not a theme archive. File not a tar.gz or tar archive." I have verified that they are all .tar.gz archives, and I have attempted to extract them and then re-archive them, but I receive the same alert message. Also, when I attempt to follow their instructions about extracting to gnome-screensaver folder, I recieve an alert that I don't have permission to complete the operation.

Any assistance would be greatly appreciated.

---

### Post by asdfhjkla on 2009-06-18
> **archangel06 said:**
> Also, when I attempt to follow their instructions about extracting to gnome-screensaver folder, I recieve an alert that I don't have permission to complete the operation.

You have to be superuser to do this.

Open a terminal and go to the directory where your .tar.gz file is. So if you have downloaded it to your Desktop folder

```

cd Desktop

```

Then open the archive manager as superuser

```

sudo file-roller **filename**
```

Where **filename** is the name of your screensaver archive.

This should open the archive manager. Now go to the "Archive" menu and click on "Extract". Find the screensaver folder (/usr/share/gnome-screensaver) and hit "Extract".

---

