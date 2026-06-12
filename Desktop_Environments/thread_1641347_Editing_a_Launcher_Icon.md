---
title: "Editing a Launcher Icon"
date: 2010-12-08
forum: Desktop Environments
---

### Post by ghormley on 2010-12-08
I created a launcher on my desktop to open a web site.  Now, I need to edit the URL.  How can I do that?

Running Ubuntu 10.10

---

### Post by Krytarik on 2010-12-09
How did you create the launcher then?

I just yet created one this way:
- find the Firefox-launcher in the Applications-menu
- right-click at it
- "add this launcher to desktop"

Then you can right-click at the newly created launcher on the desktop, click on "Properties" and enter the desired URL right behind the "firefox"-command, like this:
```
firefox http://www.google.com/
```

---

### Post by ghormley on 2010-12-09
I created the launcher by right clicking on the desktop and selecting Create Launcher.  However, when I right click on the icon as you suggest, I do not get the capability to edit the URL.

---

### Post by Krytarik on 2010-12-09
Ok, there is another way to create launcher for a web-url, obviously.
I have just done that:
- right-click on the desktop
- "Create Launcher"
- choose "Location"
- enter Name
- enter URL

When done this way, I also can't change the URL via the "Properties"-window.
But you can open the respective *.desktop-file with the Text-Editor via the "Applications"-menu and then edit the URL.:)

---

