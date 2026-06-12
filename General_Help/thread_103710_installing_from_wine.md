---
title: "installing from wine"
date: 2005-12-14
forum: General Help
---

### Post by linrasta on 2005-12-14
How do I  install a program from wine?  It is on a cd.

---

### Post by Qrk on 2005-12-14
Add 

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

To your sources list, if you haven't already.

Install wine and winetools. You can run through the wine setup using either the command winetools or winecfg. Be sure to install the windows installer from winetools. Once wine knows where your CD ROM is, you can install something off a CD just like you would in windows (with no autorun) find the installation exe.

---

### Post by aysiu on 2005-12-14
Do you already have Wine installed?
If so, double-click on the setup.exe file and install it to z:\home\linrasta\.wine\drive_c\Program Files\nameofprogram

.wine is a hidden directory, by the way.

---

### Post by linrasta on 2005-12-14
I tried to run winetools but is says:

/usr/bin/Xdialog: Error initializing the GUI...
Do you run under X11 with GTK+ v1.2.0+ installed ?
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

what do I do?

---

### Post by linrasta on 2005-12-14
I have wine installed but when I double click the exe it says "Couldn't display /media/cdrom0/setup.exe"

---

### Post by Mustard on 2005-12-14
try this in terminal

```
wine /media/cdrom0/setup.exe
```

---

### Post by linrasta on 2005-12-14
OK, I got the setup program to run, but it gives me an error saying to check the destination.  any ideas?

---

### Post by Mustard on 2005-12-14
It sounds like a wine configuration problem.

Have you run winetools and configured wine yet?

---

