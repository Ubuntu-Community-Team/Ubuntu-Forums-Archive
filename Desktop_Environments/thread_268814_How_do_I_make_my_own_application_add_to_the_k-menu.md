---
title: "How do I make my own application add to the k-menu?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by solarwind on 2006-09-30
Hi all,

I have made a a simple application in c using kdevelop. I would like to AUTOMATICALLY add it to the k menu when the application is built, (configure, make, make install). How would I do this?

---

### Post by lagagnon on 2006-10-01
You need to create a .desktop file for the application. Read the info at [www.freedesktop.org](www.freedesktop.org) and the desktop file info at the KDE website.

---

### Post by solarwind on 2006-10-13
I couldn't find out how can someone give me a link please?

---

### Post by aysiu on 2006-10-13
Go to /usr/share/applications and copy one of the desktop files there and then modify it and rename it. For example... ```
cd /usr/share/applications/kde
ls
sudo cp k3b.desktop myapplication.desktop
sudo nano myapplication.desktop
```

---

### Post by kerry_s on 2006-10-13
Right click the Kmenu icon> menu editor, right click where you want to put, choose new item, select a name, then just fill in the command. Click on the icon box to select a icon.

---

### Post by aysiu on 2006-10-13
> **kerry_s said:**
> Right click the Kmenu icon> menu editor, right click where you want to put, choose new item, select a name, then just fill in the command. Click on the icon box to select a icon.
I'm sorry you took the time to upload those screenshots, kerry_s. This is for an application the OP is developing: > I would like to AUTOMATICALLY add it to the k menu when the application is built

---

### Post by kerry_s on 2006-10-13
My bag i miss understood, i didn't realize he was talking about a whole application that would be installed. :-#

---

### Post by aysiu on 2006-10-13
I appreciate that kind of dedication to helping, though--taking and uploading screenshots takes a lot of work.

---

### Post by solarwind on 2006-10-14
Thanks a lot guys! Now I understand how to make a nice icon on the desktop. 
But how do I make it appear in the k-menu?

---

### Post by aysiu on 2006-10-14
No, the .desktop file is what makes it appear on the KMenu, not the desktop.

---

### Post by kerry_s on 2006-10-15
First you have to create the desktop file it must have ".desktop" at then end of the name.
example: app.desktop

inside the text file you put the info->

Encoding=UTF-8
Type=Application
Exec=your app
Icon=path to icon
DocPath= path to doc

Name=your apps name

Categories=where you want it in kmenu(internet,mutimedia,...)
X-Ubuntu-Gettext-Domain=put the name of app


Now you need to get that to /usr/share/applications/ so you'll need a script in your install, something like->

#!/bin/sh
cp (the app.desktop) /usr/share/applications/ 


That should get your app added to kmenu(sometimes it doesn't show till logout and back in).

I hope that helps.

---

### Post by kerry_s on 2006-10-15
> **aysiu said:**
> I appreciate that kind of dedication to helping, though--taking and uploading screenshots takes a lot of work.

It's not that hard it's just 1 button"(print), but i should wait till my eye's are fully open before i start reading posts. I had just got up from my nap and just browsed through the posts with out really reading it through. :-?

---

### Post by megamaced on 2006-10-30
So once i've created a .desktop file, how would I get it installed at the same time, alongside the program I am compiling?

Thanks

---

