---
title: "Help CLI Syntax Remove Wallpaper(s)"
date: 2014-07-03
forum: Desktop Environments
---

### Post by Kurt_Alan on 2014-07-03
****

[SIZE=5][/SIZE]

I'm doing a config after fresh install of Xubuntu 14.04.  My wallpapers are not sticking after reboot, so I want to remove some of the default wallpapers and add some of my own.  I'm hoping that a direct path will solve the problem rather than using my own folder.

If I cd to: ```
 /usr/share/xfce4/backdrops$ 
```

and I want to remove balance.jpg (as an example) and I do this:

```
  sudo apt-get remove balance.jpg 
```

I get:


```
 E: Unable to locate package balance.jpg
E: Couldn't find any package by regex 'balance.jpg'
lucas@lucas-Inspiron-1011:/usr/share/xfce4/backdrops$ 
```

How can I do this? And also, how do I use CLI to put in my own wallpapers to backdrops?

---

### Post by Frogs Hair on 2014-07-03
The wallpaper is part of a package so that is why it can't be removed with apt-get without removing the entire package. To remove individual backgrounds you could open Thunar as root and remove them manually from the usr/share folder.

In Ubuntu,in order to add wallpaper to the usr/share folder they have to be added to the .xml file in the usr/share/backgrounds folder and I don't know if that would be applicable in Xubuntu or not.

---

### Post by Kurt_Alan on 2014-07-05
**[SIZE=5][/SIZE]**

Wow! As always, I learn a lot whenever I come to the Ubuntu Forums.
From your reply, I didn't even know what Thunar was, so I googled that. Ah, that is the name of my file manager (for Xcfe). And then I wondered, what does it mean to open Thunar as root so I tried ```
 sudo thunar 
``` and there was my Thunar GUI with two warnings and root privileges. Now, not only did I take out all my unwanted default backgrounds but my personal .jpg's and .png's pasted right in, I set different wallpaper for each workspace (from Desktop Settings), Other . . . and all my wallpapers stuck after reboot. Problem solved. (There was no .xml file)

It appears that when you open Thunar as GUI non-root, that the Linux file system portion is "read only" and that even if you use sudo as in sudo apt-get that you do not have permission to write so that sudo fails.  Is that the right way to look at it?

---

### Post by Frogs Hair on 2014-07-05
One reason the root file system requires elevated permissions is to protect files vital to the operating system from unwanted tampering intended or otherwise.

---

