---
title: "LXDE desktop folder link"
date: 2010-01-27
forum: Desktop Environments
---

### Post by david2m3h on 2010-01-27
Installed lxde on top of Ubuntu minimal install just to try it out. I like it so far. 

There is one thing I would like to change but have not figured out how. By default the desktop has a "folder link" or "launcher" (shortcut for those of us more familiar with windows) linked to my user My Documents folder.

I like a clean desktop and would like to remove this "folder link" but it is owned by "root". I have not been able to find a way to change the permissions to allow me to remove it from my desktop. Any help would be much appreciated.

---

### Post by david2m3h on 2010-01-27
After doing a little research it appears this My Documents desktop icon is written into the source code for the PCManFM which is what LXDE uses to manage the desktop.

According the to roadmap goals for PCManFM the ability for the user to hide such "virtual items" on the desktop will eventually be an option in a future release of LXDE - link [http://wiki.lxde.org/en/PCManFM_Roadmap]("http://wiki.lxde.org/en/PCManFM_Roadmap") (see desktop icons section).

This appears to be beyond my ability to remove.

---

### Post by david2m3h on 2010-01-28
Solved for me anyway.

There is an option that works for me. Open PCManFM and go to Edit > Preferences > Desktop. There is an option "Manage the desktop and show icon files". Turning this off removes all icons from the desktop.

This option works for me as I want a clean desktop. Of course this leaves me with no icon management for my desktop, but I don't need any icons on this desktop anyway (or want them).

---

