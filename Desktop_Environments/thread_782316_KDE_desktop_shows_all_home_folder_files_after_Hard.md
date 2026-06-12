---
title: "KDE desktop shows all home folder files after Hardy upgrade"
date: 2008-05-04
forum: Desktop Environments
---

### Post by fixitdude on 2008-05-04
The icons on my desktop are now all the folders and files in my home folder, they are NOT simply links to the files, like symbolic links, they are the actual files, if I delete one it's actually gone from the HD, very annoying.

I had only a few icons on Gutsy before the upgrade. The desktop is behaving like a file browser or like when you click on the "home" icon.

Looked at settings for KDE and looked for obvious .kde/share/config like files that may have an answer with no luck.

---

### Post by GeneralZod on 2008-05-05
KDE's desktop has always acted in this way i.e. as a file manager; the problem here is that for some reason it is now rooted at ~ rather than ~/Desktop.

Check System Settings->System Administration->Paths and ensure that Desktop Path is ~/Desktop.

---

### Post by fixitdude on 2008-05-06
> **GeneralZod said:**
> KDE's desktop has always acted in this way i.e. as a file manager; the problem here is that for some reason it is now rooted at ~ rather than ~/Desktop.

Check System Settings->System Administration->Paths and ensure that Desktop Path is ~/Desktop.Thanks. That fixed it after a reboot.

---

### Post by jtappin on 2008-07-01
> **GeneralZod said:**
> 
Check System Settings->System Administration->Paths and ensure that Desktop Path is ~/Desktop.

I think that should be:
System settings -> About Me -> Paths

And if it insists on trying to move your whole home directory to ~/Desktop and then shows the contents of / on your desktop then you can try editing ~/.config/user-dirs.dirs and changing the definition of XDG_DESKTOP_DIR to:
XDG_DESKTOP_DIR="$HOME/Desktop/"

---

