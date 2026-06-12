---
title: "Desktop folder gets deleted on logout or login"
date: 2011-03-18
forum: Desktop Environments
---

### Post by bnebb on 2011-03-18
Ubuntu 10.04.  Also have Kubuntu desktop installed.  Usually use Ubuntu.

Home folder shows as the desktop.  Checked settings for Nautilus, Home_folder_is_Desktop is NOT checked.  ~/Desktop folder does not exist.  .config/user-dirs.dir desktop line is set to XDG_DESKTOP_DIR="$HOME/"

So, created the ~/Desktop folder.  Changed the line in user-dirs.dir to read XDG_DESKTOP_DIR="$HOME/Desktop".  Log out.  Log back in.  Result:

Home folder shows as the desktop.  Checked settings for Nautilus, Home_folder_is_Desktop is NOT checked.  ~/Desktop folder does not exist.  .config/user-dirs.dir desktop line is set to XDG_DESKTOP_DIR="$HOME/"

Logged into the KDE desktop.  It complains that the ~/Desktop folder does not exist.  Shows nothing on the desktop.  Create the ~/Desktop folder.  Set KDE to use the ~/Desktop folder.  Check .config/user-dirs.dir and make sure that the Home folder shows as the desktop.  Checked settings for Nautilus, Home_folder_is_Desktop is NOT checked.  ~/Desktop folder does not exist.  .config/user-dirs.dir desktop line is set to XDG_DESKTOP_DIR="$HOME/Desktop" line is in.  Everything is set.  Log out.

Log in to Ubuntu.  Result:

Home folder shows as the desktop.  Checked settings for Nautilus, Home_folder_is_Desktop is NOT checked.  ~/Desktop folder does not exist.  .config/user-dirs.dir desktop line is set to XDG_DESKTOP_DIR="$HOME/"

This problem showed up on two computers after a clean install of Ubuntu 10.04 followed by an install of the Kubuntu desktop.  Might as well install Kubuntu desktop because some of the utilities I like to use (Kate, Krusader, etc) require that major parts of it be installed anyway.  

What appears to be happening is that the user-dirs.dir folder is getting ignored and is overwritten either on logout or login and the ~/Desktop folder is being deleted.

Now, can anyone help?  This appears to be a major conflict with Kubuntu and Ubuntu on the same machine even though you should be able to switch desktops without problem.


Bnebb.
Not exactly a newbie

---

### Post by Krytarik on 2011-03-19
Try this:
- create the "~/Desktop" directory
- use "Ubuntu Tweak" to set the directory as your desktop folder
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```You will find Ubuntu Tweak in "Applications -> System Tools" after the installation.
In it choose "Default Folder Locations" in the section "Personal".

---

### Post by bnebb on 2011-03-19
Thanks for the suggestion.  I had already downloaded Ubuntu Tweak.  I did as you suggested.  Then I logged out.  Result?  I get the same action as before.  The ~/Desktop folder gets deleted and the desktop is the Home folder.

Something deletes that Desktop folder.  I don't know if it is in log out or login.  Checking the .config file, it shows that the Desktop folder should be ~/Desktop.  The user-dirs.dir file, though, shows that the Desktop should be the Home folder.

Does anyone have a clue as to what is making these changes?

---

### Post by Krytarik on 2011-03-20
I did a forums search on it, and I have a guess right now:

Do you have different locales at your system, or did you switch from one to another recently?

Is the item "User folder update" enabled in "Startup Applications"? If so, does it matter when you disable it?

What does the command
```
xdg-user-dirs-gtk-update
```
when you run it right after creating the "Desktop" directory and setting ".config/user-dirs.dir" right? It is the same command also run by "User folder update".

What is the content of ".config/user-dirs.locale"?

---

### Post by bnebb on 2011-03-20
Absolutely nothing happens when I create the Desktop folder and update user-dirs.dirs and then run the command.  The desktop shown is still the home folder.  After logging out and logging back in, the Desktop is again the Home folder and the Desktop folder is deleted.  The user-dirs.dirs file again shows the Desktop to be the Home folder.

This is the case even though the User Update is disabled on startup.

The user-dirs.locale content is en-US

This thing really baffles me.  Something deletes the Desktop folder and changes the user-dirs.dir file.

Any more suggestions?  I haven't found anything anywhere as yet.  Maybe I'm not asking the right question.  But, since it has occurred on at least three clean installs, it's got to be a bug somewhere.

---

### Post by Krytarik on 2011-03-21
Is *any* *new* file retained after re-login?

Is the deleted "Desktop" folder still somewhere, like in "~/.local/share/Trash/files" (just search for its name)?

You may try removing the packages
- "xdg-user-dirs"
- "xdg-user-dirs-gtk"

You may report a bug here:
- [https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs)
- [https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs-gtk](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs-gtk)

---

### Post by bnebb on 2011-03-21
The Desktop file is not in the trash bin.  It just gets deleted.  I'm going to examine the startup and shutdown files and see what might be deleting the Desktop folder.  One thing I might try is to remove the KDE desktop because all this stuff started after KDE was installed.

If you have any other ideas, I'll welcome them.  Thanks for the help you've provided.

---

