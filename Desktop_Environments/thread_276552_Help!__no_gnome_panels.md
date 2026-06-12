---
title: "Help!  no gnome panels"
date: 2006-10-13
forum: Desktop Environments
---

### Post by scannerdarkly on 2006-10-13
ok so i accidently delete the gnome panel appelet and i need it back.  can anybody help!?!

---

### Post by Rhubarb on 2006-10-13
I'm not in front of my ubuntu box at the moment (at work using m$), but I think all you need to do is right click on the desktop or the bottom panel, then select "Add Panel".
That's it.

---

### Post by scannerdarkly on 2006-10-13
what i mean is the actual gnome-panel program or script or whatever it is got deleted or shall i say uninstalled.

---

### Post by Rhubarb on 2006-10-13
Oh, that's kinda bad then.
Hit Alt + F2 to get you into the terminal, then try
```
sudo apt-get install gnome-panel
```
Again the "gnome-panel" bit might be wrong as I'm not in front of my ubuntu box at the moment.
Another way is to open up synaptic and do a search for "panel" and install it.  Doing a sudo synaptic should open up the package manager for you.
```
sudo synaptic
```

---

### Post by scannerdarkly on 2006-10-13
ok i'll try that when i get home, i'm at work too and my laptop battery just died so i'm stuck right now, but thanks

---

### Post by Caboose01 on 2007-10-16
HELP!!! also have no Gnome panels, every time i log in there are no panels - top or bottom
I have ruled out the following:

    * The panels are not being cut off the edge of the screen, i can see the cursor the whole way around.
    * Corrupt installation of Ubuntu, i have re-installed it.

The problem with your solution using Alt+F2 is that no terminal comes up!
Please help, i don't think Gnome is un-installed but it might be.

---

