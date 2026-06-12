---
title: "Wolfenstien Enemy Territory"
date: 2009-02-11
forum: Gaming &amp; Leisure
---

### Post by unplugged23 on 2009-02-11
Hey there,

No matter where i try to install this game it says i dont have write permission. how should i fix this?

---

### Post by Azure.Rise on 2009-02-12
Are you running the installer using the sudo command?

---

### Post by noerrorsfound on 2009-02-12
(**too late**)

Either install somewhere in your home folder (the installer should let you type your own path) or start it through the console and prefix the command with **sudo**.

---

### Post by wolfyking2 on 2009-02-12
Ok, right click the installer/runner.  Go to properties, then go to the tab permissons.  An interface should come up, leave all that alone.  At the bottom you'll see a little box.  If the box is unchecked, check it.  If the box is checked...then I don't know what to do:lolflag:

---

### Post by donkyhotay on 2009-02-12
If you installed with sudo so all users can play it (which it sounds like you did) you'll need to change the permissions of the folder with
```
sudo chmod 777 -R /path/to/ET
```
otherwise if you are the only user playing then install without the sudo command within your home folder.

---

