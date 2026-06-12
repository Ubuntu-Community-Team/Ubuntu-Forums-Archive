---
title: "CHMOD Filesystem?"
date: 2005-12-21
forum: Desktop Environments
---

### Post by Blind on 2005-12-21
I have one username on my computer...mine, I am running Ubuntu 5.10 (newest) and installed last night. I need to copy files into my etc, opt, and usr folders. When I drag the files from file browser into the filesystem I get the:
> **Error while moving to '/'**
you do not have permission to write to this folder

When I right click filesystem and go to 
```
Properties -> Permissions 
```
I can not change any because "I am not the owner" although I am the only user on the computer.

Help?

---

### Post by Spudgun on 2005-12-21
You'll have to move the files as root.

---

### Post by Blind on 2005-12-21
Do I log in as user 'root' with what password? I just installed and made one name during the install...which is the name I am on, and have tried moving them on.

---

### Post by frodon on 2005-12-21
Ubuntu use sudo instead of root account, read that : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)
So the default password for sudo is you user password.
If you want to use the file browser as root, use this command line : ```
gksudo nautilus
```

---

### Post by Blind on 2005-12-21
[QUOTE=frodon]Ubuntu use sudo instead of root account, read that : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)
So the default password for sudo is you user password.
If you want to use the file browser as root, use this command line : ```
gksudo nautilus
```[/QUOTE]
When I go to filebrowser as root, I can't cmod successfully, I get:

> **The permissions could not be changed.**
Sorry, couldn't change the permissions of "Filesystem".

do I chmod though sudo somehow?

---

### Post by frodon on 2005-12-21
Ok, could you give us some details.
First what are you trying to chmod and why ? In the ubuntu partition you need root rights to perform a chmod (except in your home directory), so indeed you will need sudo to do that.

---

### Post by aysiu on 2005-12-21
[QUOTE=Blind]When I go to filebrowser as root, I can't cmod successfully, I get:



do I chmod though sudo somehow?[/QUOTE] You don't chmod. When you type in ```
gksudo nautilus
``` a file browser **with root privileges** pops up. Go to the folder you want and copy and paste, rename, drag and drop... whatever you need to do--all with your mouse!

After *gksudo nautilus* you don't need the terminal any more.

---

### Post by thespazzz on 2005-12-21
I don't think you CAN change the permissions on the entire filesystem anyway.  Nor would you want too.  That's pretty much what makes the root acccount the root account.

In any event you shouln't need to change permissions anyway.

SUDO means basicly SUPER USER DO.  Think of it as the "Run Application as another user" option in windows.  Nautulus is the file browser for Gnome,  the windows version of "explorer.exe"  SO once you open that window you anything you open or do from that particular window you do as ROOT.

---

