---
title: "Add executable to Favorite bar"
date: 2019-12-23
forum: Desktop Environments
---

### Post by py-ohayo on 2019-12-23
Hello,
I want accelerate access to a framework that I've just installed.
The executable is not in the list of applications.
How to proceed ?
Thanks.

---

### Post by Dennis N on 2019-12-23
You do not identify your OS, so suggestions here would be just guesswork. Please provide OS name and release. For example: Ubuntu MATE 18.04

---

### Post by vanadium on 2019-12-23
You need to copy the .desktop file that launches the "framework" to `~.local/share/applications'. Then, it will appear in the menu for the current user. To make the program available for all users of the system, copy the .desktop file to '/usr/local/share/applications'.

If your application does not come with a .desktop file (i.e., a launcher), then you can create one your self. A launcher is a text file containing instructions on how to launch the program and display it in the application menu. See for example [rl=http://xmodulo.com/create-desktop-shortcut-launcher-linux.html]here[/url] for instructions on how to create a launcher yourself.

---

### Post by py-ohayo on 2019-12-29
> **Dennis N said:**
> You do not identify your OS, so suggestions here would be just guesswork. Please provide OS name and release. For example: Ubuntu MATE 18.04

NAME="Ubuntu"
VERSION="18.04.3 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.3 LTS"
VERSION_ID="18.04"

---

### Post by py-ohayo on 2019-12-29
> **vanadium said:**
> You need to copy the .desktop file that launches the "framework" to `~.local/share/applications'. Then, it will appear in the menu for the current user. To make the program available for all users of the system, copy the .desktop file to '/usr/local/share/applications'.

If your application does not come with a .desktop file (i.e., a launcher), then you can create one your self. A launcher is a text file containing instructions on how to launch the program and display it in the application menu. See for example [rl=http://xmodulo.com/create-desktop-shortcut-launcher-linux.html]here[/url] for instructions on how to create a launcher yourself.

I've tried it. Here is content of **.desktop** file (that I created) in **~/.local/share/applications**:
[Desktop Entry]
Comment=ModusToolbox
Terminal=False
Name=ModusToolbox
Exec=~/P-ModusToolbox_2.0.0.1703-linux-install/ModusToolbox/ide_2.0/eclipse/ModusToolbox
Type=Application
Icon=~/P-ModusToolbox_2.0.0.1703-linux-install/ModusToolbox/ide_2.0/eclipse/icon.xpm
StartupWMClass=Eclipse

Doesn't work - **ModulToolbox** doesn't appear in application pool

---

### Post by vanadium on 2019-12-29
Replace "~" by the full path of your home directory.

---

### Post by py-ohayo on 2019-12-30
Thanks !!!

---

