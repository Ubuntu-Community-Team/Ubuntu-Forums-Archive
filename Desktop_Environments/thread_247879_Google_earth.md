---
title: "Google earth"
date: 2006-08-31
forum: Desktop Environments
---

### Post by sheda on 2006-08-31
I have downloaded google earth qnd have a number of .bin files on the desktop. What shall I do with them? (I`m new to this):confused: 
thanks in advance

---

### Post by phido on 2006-08-31
Run in a console 
*sh GoogleEarthLinux.bin* 
to install it for single user or [I]
sudo sh GoogleEarthLinux.bin[/I] 
for global install.
When installing with sudo, dont run it out of the installer the first time.

Edit: Here is a [thread]("http://www.ubuntuforums.org/showthread.php?t=195335") about GEarth install

---

### Post by sheda on 2006-08-31
Thqnx for the reply. Unfortunqtely, when I said I`m new to this read it as `doesn`t have a clue`. I got as far as clicking on the desktop icon, then a window opened saying something about encoding but I couldn`t figure out how to put any of the strings in that were posted previously or in here. I`m no further forward. Please excuse my ignorance...:-(

---

### Post by phido on 2006-08-31
> **sheda said:**
> Thqnx for the reply. Unfortunqtely, when I said I`m new to this read it as `doesn`t have a clue`. I got as far as clicking on the desktop icon, then a window opened saying something about encoding but I couldn`t figure out how to put any of the strings in that were posted previously or in here. I`m no further forward. Please excuse my ignorance...:-(

Ok :rolleyes:
Open a shell/console/terminal with "Applications - Accessoires - Terminal"
A good introduction can be found [here]("http://linuxcommand.org")

If the GoogleEarthLinux.bin is on your Desktop, lets go there.
```
cd Desktop
``` ^^ in the console ;)

Hint: You can autocomplete filenames/commands by pressing "Tabulator"-Key

Allow executing of the file
```
chmod +x GoogleEarthLinux.bin
``` and run it with
```
sudo sh GoogleEarthLinux.bin
``` You have to provide your user-password for sudo (Superuser).

Let the Installer run and exit, do not start it.

Now you can find GoogleEarth, under "Applications - Internet - GoogleEarth"

** You need a graphics card (driver) with 3D acceleration to run it smooth.**

---

### Post by sheda on 2006-09-02
Many thanks, I follolwed your instructions and it works fine! =D>

---

