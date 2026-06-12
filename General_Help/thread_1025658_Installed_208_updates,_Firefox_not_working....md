---
title: "Installed 208 updates, Firefox not working..."
date: 2008-12-30
forum: General Help
---

### Post by dflynn on 2008-12-30
I tried searching the forums for this but couldn't find anything to give me an results.
I recently installed Ubuntu 8.10 with Gnome on my parents computer and got everything set up, then installed the 208 updates that it said it needed. 
I woke up this morning and it wasn't responding so I reset the computer and everything loaded just fine.

Then a popup said that "Power Manager settings with Gnome hadn't been set..."  something like that.

So I tried to open Firefox to get some answers but Firefox doesn't open. It opens a little tab in the toolbar at the bottom of the screen but then closes. 
So I tried the help button, and same thing happens.

Mail programs work fine though. 

Any ideas what is going on and how I can fix these three issues?

Thank you.

Oh, I should mention I'm pretty new to Linux so if you could try to spell things out, thatwould be great :D

---

### Post by eBoxNet on 2008-12-30
you can try to remove and re install firefox.

```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox
```

---

### Post by gettinoriginal on 2008-12-30
Power management is System > Pref > Power Management
For the Firefox issue, in terminal:
```
Firefox
```
and see what it tells you

---

### Post by dflynn on 2008-12-30
I tried what you said but terminal says:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

---

### Post by eBoxNet on 2008-12-30
run in terminal : ```
sudo dpkg --configure -a
```


it looks that some packages having troubles after the update,this will hopefully fix it.

---

### Post by dflynn on 2008-12-30
Ok, I opened the power management and it the bubble came up again. Here's exactly what it said:


Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator.

---

### Post by dflynn on 2008-12-30
> **gettinoriginal said:**
> Power management is System > Pref > Power Management
For the Firefox issue, in terminal:
```
Firefox
```
and see what it tells you

When i put firefox in terminal it says:

```

Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

```

---

### Post by dflynn on 2008-12-30
> **eBoxNet said:**
> run in terminal : ```
sudo dpkg --configure -a
```


it looks that some packages having troubles after the update,this will hopefully fix it.


Ok I'm running this now.

---

### Post by dflynn on 2008-12-30
Ok that last bit of code seems to have gotten firefox working. :D
Here's hope for everything else!


Edit:

Perfect. No more notifications. It all seems to be working. Thank you eBoxNet and Gettinoriginal

---

### Post by eBoxNet on 2008-12-30
EDIT : Happy to help ;) you are welcome.

mark as solved pls

---

