---
title: "Unity launcher and .desktop files"
date: 2013-01-29
forum: Desktop Environments
---

### Post by johnaaronrose on 2013-01-29
Not sure if I should start a new thread for this question. I created a folder (in my home folder) to hold my .desktop files before installing them in the Unity Launcher. I did not copy them to /usr/share/applications or ~/.local/share/applications. Instead I dragged them from Nautilus to the Unity Launcher. I've tried to delete them by Unlocking them from the Launcher. But that removes them from the Launcher but they are still in the Launcher list created by: gsettings get com.canonical.Unity.Launcher favorites

For example, one entry listed by that command is:
'/home/john/Launchers/Magnifier.desktop'

How can I remove these erroneous entries?

---

### Post by johnaaronrose on 2013-01-29
I'm so fed up with running CLI stuff for creating/modifying/validating/installing that I'm now writing a GUI for these fuctions.

---

### Post by oldos2er on 2013-01-29
Posts moved to their own thread.

---

### Post by johnaaronrose on 2013-01-30
I've written a GUI for creating, modifying, validating, installing &  uninstalling Desktop Configuration Files in Ubuntu. It's written in  Gambas3. It should pull down the required Gambas3 components (if there's  a version/dependency problem on installation, you may need to add  nemh's Gambas3 ppa (see [https://code.launchpad.net/~nemh/+archive/gambas3]("https://code.launchpad.net/%7Enemh/+archive/gambas3")) to your Software Sources when installing it by use of Software Centre or gdebi after downloading it from the link below:
[http://dl.dropbox.com/u/3928731/maintaindesktopconfigurationfiles.deb](http://dl.dropbox.com/u/3928731/maintaindesktopconfigurationfiles.deb)

---

