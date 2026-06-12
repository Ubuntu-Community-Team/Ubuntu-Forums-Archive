---
title: "Missing ICONS on Ubuntu"
date: 2008-07-16
forum: Desktop Environments
---

### Post by kaola_linux on 2008-07-16
I've attached a screenshot of my desktop after I've deleted the contents of my pixmaps folder, now I can't revert it back.Can someone help me restore them?


Plz help me plz...

---

### Post by forger on 2008-07-16
pixmaps of which package?
you mean the folder **/usr/share/pixmaps** ? there are a lot of packages that install files in that folder

---

### Post by kaola_linux on 2008-07-16
yes that one..ive rm'd it...accidentally

---

### Post by forger on 2008-07-16
well it's too big :)

Find all your packages and try to reinstall them:
**[COLOR="Red"]WARNING! Can break stuff!! Use at your own risk![/COLOR]**

```
sudo apt-get install --reinstall `apt-cache dump | grep Package: | sed -e 's/Package: //' | xargs`
```

---

### Post by kaola_linux on 2008-07-16
> **forger said:**
> well it's too big :)

Find all your packages and try to reinstall them:
**[COLOR="Red"]WARNING! Can break stuff!! Use at your own risk![/COLOR]**

```
sudo apt-get install --reinstall `apt-cache dump | grep Package: | sed -e 's/Package: //' | xargs`
```

do i have to enter the code you provided on the terminal? I've tried it but it gives me an error

---

### Post by Superevil on 2008-08-26
wow I just did the same stupid thing recently. still havent figured out a fix yet

---

### Post by mgmiller on 2008-08-27
boot off a live cd and then enter a root browser:
```
gksu nautilus
```
You can now browse to /usr/share/pixmaps in the virtual image of the live cd and copy it to the /usr/share/ of your hard drive.

Be careful as you are in su mode and you can really frak your installed OS.  So just be sure you are copying stuff from and to where you really want to.

---

### Post by Superevil on 2008-08-27
nope that didnt work either

---

### Post by mgmiller on 2008-08-28
If you deleted the entire pixmaps folder from your hard drive, what I suggested should work to restore it.  Any images that were put there by other packages you installed can be restored by reinstalling the package after you copy over the new pixmaps folder.  

Are you sure you browsed to the /usr/share/pixmaps in the file tree while running the live cd and copied it to the right spot on your hard drive?  When in live cd mode, your hard drive would be in /media.  Once you open that, you should see the whole file tree of your drive.

---

### Post by Superevil on 2008-08-28
yea I'm sure I copied the right folder. I thought I might have had the problem fixed when i downloaded and installed the hicolor icons which fixed most of the missing ones but the icons for ccsm, compiz-icon, screenlets, awn, pidgin, liferea, network icon, and sound converter.

---

### Post by mgmiller on 2008-08-28
The hicolor-icons install to /usr/share/icons  not pixmaps.  Perhaps, you can do a compare side by side of all the contents of /usr/share/icons between the live cd and your installation.  Applications that are not displaying their icons correctly might get fixed by doing a complete uninstall followed by a reninstall, rather than just doing the reinstall.

---

### Post by Superevil on 2008-08-29
it seems my issue has nothing to do with /usr/share/pixmaps, it was something I deleted in /usr/share/icons

---

