---
title: "Unity Configuration"
date: 2014-04-18
forum: Desktop Environments
---

### Post by cranerja on 2014-04-18
Hello, I am wondering where Unity's configuration files are saved. I can't seem to find a clear enough answer online. The goal is to sync the file(s) across all my computers so all users will have their own desktop. I will be using 14.04.

---

### Post by mcduck on 2014-04-18
As far as I know it stores it's settings in dconf (which has a single binary file in ~/.config/dconf/user) , so there are no text-based configuration files around.

This of course means that you can't just copy the file around since it stores a lot more stuff than just Unity settings. You can still do dome stuff with mandatory dconf values and such if you really want (which would force certain settings on all users): [https://wiki.gnome.org/action/show/Projects/dconf/SystemAdministrators?action=show&redirect=dconf%2FSystemAdministrators]("https://wiki.gnome.org/action/show/Projects/dconf/SystemAdministrators?action=show&redirect=dconf%2FSystemAdministrators")

---

### Post by cranerja on 2014-04-18
Oh, alright thanks. So even soft linking one user file from all computers wouldn't work? Sorry I don't know too much about it

---

### Post by grahammechanical on 2014-04-18
Some user configuration files are in /home/username/  There will be a folder for each user in /home. It will have certain user settings for the desktop and applications. They will be hidden files with a dot ( . ) before the name of the file or folder. You will need to set the File Manager to show hidden files to see them. You may find some of the stuff you are looking for there. How useful this information will be, I cannot say.

Keep in mind as users go from machine to machine the files in /home/username/ will change and be different on different machines.

Regards

---

### Post by cranerja on 2014-04-18
I know where application settings are, I'm looking for unity's. What my objective is will be having all accounts be identical on each machine. I've already got files working from a server, just looking for desktop configuration. Thanks anyway

---

