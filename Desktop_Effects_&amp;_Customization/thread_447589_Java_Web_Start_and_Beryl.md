---
title: "Java Web Start and Beryl"
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by ozorba on 2007-05-18
Does anyone know why nothing appears (blank window) in the java apps windows opened with javaws in Beryl?

There are not any problems when I disable Beryl. The java windows work fine.

---

### Post by Kobalt on 2007-05-18
Open up your /etc/profile file 
```
gksu gedit /etc/profile
```
And add the following line at the end of the file : > export AWT_TOOLKIT="MToolkit"
Then go to your Home folder, press Ctrl+Alt+H to see hidden files and open up .bashrc. Add the above line at the end of the file as well. Reboot, and voilà :)

---

