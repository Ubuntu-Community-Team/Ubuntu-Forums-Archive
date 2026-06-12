---
title: "Ubuntu 24.04 - How do I change the file-application association?"
date: 2024-11-19
forum: Desktop Environments
---

### Post by a2-koray on 2024-11-19
Previously it was possible to do this within nautilus by selecting file properties, "Open with...". Now I can't find a way doing this. I've checked in the "Settings" app. There's a "Default Apps" section but it only shows generic associations rather by than file extension. What's the current way of changing the file association?

My specific problem is that I would like to open .csv file with a specific application, unfortunately, whenever I double click it will open LibreOffice Calc which is not the app I want to use for these files. So every time I have to click "open with other application" then click on the application I want to use, but I can't see any option to set the selected app as "default".

---

### Post by Holger_Gehrke on 2024-11-20
The tool 'xdg-mime' on the command line should allow you to do that. Use 'xdg-mime query filetype path/and/name-of-the-file' (replace the obvious placeholder ...) to get the exact name of the mime-type of the file then use 'xdg-mime default name-of-the-desktop-file mime-type' to set the program for which you give the name of the desktop file as the default for that mime-type.

Holger

---

### Post by jon-sh on 2024-12-09
Is there a way to find out the application currently associated with a mime type? xdg-mime does not do it. Where are configs (eg conig text file) held?

---

### Post by jon-sh on 2024-12-09
It seems to be listed in .config/mimeapps.list The applications are identified by their .desktop file (ie in /usr/share/applications )

 eg  

 application/pdf=libreoffice-draw.desktop;org.gnome.gedit.desktop;org.gnome.Evince.desktop;

 
 
 The default one for pdf (ie when you double-click on it) is: evince &#8211; gnome document viewer (built-in). Another file must determine that this be used?

---

### Post by a2-koray on 2024-12-10
The help of xdg-mime isn't very helpful but you can actually do something like:

```
xdg-mime query default text/csv
```

---

