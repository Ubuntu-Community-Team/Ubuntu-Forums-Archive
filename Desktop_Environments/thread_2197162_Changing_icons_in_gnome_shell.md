---
title: "Changing icons in gnome shell"
date: 2014-01-02
forum: Desktop Environments
---

### Post by orj-gmail on 2014-01-02
How can i change icons in the gnome shell? there are some programs which come with very pixelated icons (in the shell) for example klavaro, grisbi, gnome-paint, glabels and clementine. Changing these icons with alacarte don't work. Is there a file to edit for changing the icon? Other icons are changeable with alacarte. My icon set has icons for all these programs but i can#t makethem to show up on the desktop. Any idea?

---

### Post by Frogs Hair on 2014-01-02
Hello and Welcome 

I use alacarte / main menu to apply custom icons in both the Gnome Shell and  Unity(13.10) . When you write that it doesn't work I'm not sure what you mean. Some application icons are stored usr/share/pixmaps or other folders and the quality of those icons varies from poor to better.
 
Through the main menu I select the icon image in launcher properties and navigate to the file which contains the image I want to use. If the set you are using has icons for the applications the path would be File System > usr/share/icons. If the applications are added to favorites you need to remove them and add them or log-out and in to see the image change.  The pictured icon is not the one provided with the pithos application, but added with the main menu as described.

---

### Post by orj-gmail on 2014-01-02
> **Frogs Hair said:**
> Hello and Welcome 

I use alacarte / main menu to apply custom icons in both the Gnome Shell and  Unity(13.10) . When you write that it doesn't work I'm not sure what you mean. Some application icons are stored usr/share/pixmaps or other folders and the quality of those icons varies from poor to better.
 
Through the main menu I select the icon image in launcher properties and navigate to the file which contains the image I want to use. If the set you are using has icons for the applications the path would be File System > usr/share/icons. If the applications are added to favorites you need to remove them and add them or log-out and in to see the image change.  The pictured icon is not the one provided with the pithos application, but added with the main menu as described.

Thank you for answering. I did like you described it (alacrte let me choose another icon but the icon is not showing up and when i open alacarte a second time There no icon). This happens only with icons of the above mentioned applications.
With all others it woks like you described and i did several times. For this reason i wanted to know an altrnative way to change these icons.

---

### Post by Frogs Hair on 2014-01-02
You could try changing the image directly in computer> usr/share/applications if displayed there , but to change items in the file system you need root permission.Open the file browser with the command below . Use caution when poking around the file system and if you are not sure leave well enough alone.
 
The main menu is the safest way to accomplish the task and I don't know why it is not working unless  those applicators use a different image type. I have had to rename some of my custom icons on occasion but those were stored in my home folder and not the root file system .  

```
gksudo nautilus 
```

---

### Post by orj-gmail on 2014-01-03
Tried to change in /usr/share/applications...didn't work. In /.local/share/applications I found the files to change. Solved now. Thank you for your help.

---

### Post by Frogs Hair on 2014-01-03
The correct folder can be elusive depending  on the application/s . Glad it's sorted out. :)

---

