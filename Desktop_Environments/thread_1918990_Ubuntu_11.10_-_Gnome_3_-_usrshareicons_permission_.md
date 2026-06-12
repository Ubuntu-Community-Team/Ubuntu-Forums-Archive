---
title: "Ubuntu 11.10 - Gnome 3 - /usr/share/icons permission for cursor theme"
date: 2012-02-02
forum: Desktop Environments
---

### Post by Moofy on 2012-02-02
So i am running Ubuntu 11.10 with Gnome 3 ATM.

I found this cursor set: [http://gnome-look.org/content/show.php/Pulse+Glass?content=124442](http://gnome-look.org/content/show.php/Pulse+Glass?content=124442) that i want.
When i go to: /file-system/usr/share/icons and want to paste it there i get permission denied, i have tried using the terminal code
```
gksu nautilus
```But still no acces.

Any help?

---

### Post by Toz on 2012-02-08
Hello and welcome to the forums.

If this icon set if for your use only (not system-wide), you can place it in a directory called **.icons** in your home directory (they will be recognized by the system). That directory may not exist and may need to be created (it is also a hidden directory - you'll need to set nautilus to show hidden files/folders).

If you want it to be set system-wide, you will need to copy them to /usr/share/icons. Not sure why gksu nautilus didn't work for you. If you want to try via command line, the command would be:
```
sudo cp -r /path/to/Pulse-Glass /usr/share/icons
```
...make sure you change /path/to to the actual path to the folder.

---

### Post by Moofy on 2012-02-09
> **Toz said:**
> Hello and welcome to the forums.

If this icon set if for your use only (not system-wide), you can place it in a directory called **.icons** in your home directory (they will be recognized by the system). That directory may not exist and may need to be created (it is also a hidden directory - you'll need to set nautilus to show hidden files/folders).

If you want it to be set system-wide, you will need to copy them to /usr/share/icons. Not sure why gksu nautilus didn't work for you. If you want to try via command line, the command would be:
```
sudo cp -r /path/to/Pulse-Glass /usr/share/icons
```...make sure you change /path/to to the actual path to the folder.It is still not possible for me, i don't get a error or anyting.

---

### Post by Toz on 2012-02-09
Which method did you try? The ~/.icons method or the /usr/share/icons method? 

Can you post back the commands and results you got along with the results of the following:
```
ls -l ~/.icons
ls -l /usr/share/icons
```

---

