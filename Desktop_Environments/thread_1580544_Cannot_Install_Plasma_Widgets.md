---
title: "Cannot Install Plasma Widgets"
date: 2010-09-23
forum: Desktop Environments
---

### Post by Faylcon on 2010-09-23
I am running Ubuntu 10.10 prerelease and KDE 4.5.1.  Using the download new widgets option, the widgets do not install.  They are listed as installed, but are not available.  Downloading a .plasmoid file seems to work when manually installing.  Any ideas?

---

### Post by ankspo71 on 2010-09-23
Hi,
Unless you are experiencing something different, this is probably because the plasmoids weren't packaged the same way that KDE knows how to unpack them for us, so we have to manually install them. This can apply to many other theme-like items, service menus, plasmoids, etc.
 
So for the plasmoids that didn't install go look inside:
/home/yourname/.kde/share/apps/plasma/plasmoids/
and make sure they each only have one main plasmoid folder.

Correct installation:
/home/yourname/.kde/share/apps/plasma/plasmoids/"plasmoid-main-folder"/theme-contents

Not correct installation:
/home/yourname/.kde/share/apps/plasma/plasmoids/"plasmoid-main-folder"/[COLOR="Red"]"another-plasmoid-main-folder"[/COLOR]/theme-contents
(These extra un-needed folders can prevent alot of things from installing correctly.)
Hope this helps.

---

### Post by Faylcon on 2010-09-29
After the last system update, the problem with installing widgets has been solved.  Must have been a bug.

---

