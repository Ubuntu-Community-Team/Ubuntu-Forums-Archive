---
title: "Desktop Icons at bottom of screen !?"
date: 2009-03-18
forum: General Help
---

### Post by dejay68 on 2009-03-18
Hi,
I have seen some screenshots of desktop wallpaper with the icons in the middle of the screen, at the bottom. Is this a theme addon or is it a setting within compiz ?
Thanks.

---

### Post by lvleph on 2009-03-18
Maybe you are referring to avant-window-navigator. How about posting a screen shot.

---

### Post by dejay68 on 2009-03-18
avant .... thats it - thanks, now just got to work out how to make it opaic over my desktop.

---

### Post by zigx on 2009-03-18
If the screen shot attached is what you want, bust open a terminal and do:

```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main'  |  sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update
```
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

taken from [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by zigx on 2009-03-18
damn, one minute too late! lol

---

### Post by dejay68 on 2009-03-19
Any idea how i have avant over the top of open windows ? At the moment it is squishing my desktop by insisting to appear below any open window :popcorn:

---

### Post by dejay68 on 2009-03-19
sorted that problem now for another !!! how do i ensure avant starts each time i turn on my pc ? for some reason i have to start it from the accessories tab every time.

---

### Post by Lunx on 2009-04-02
> **dejay68 said:**
> sorted that problem now for another !!! how do i ensure avant starts each time i turn on my pc ? for some reason i have to start it from the accessories tab every time.

I'm keen to find the answer to this as well if anyone has the solution.

---

### Post by CatKiller on 2009-04-03
System -> Preferences -> Sessions is the easiest way to have a program automatically start at login.

---

### Post by Lunx on 2009-04-03
> **CatKiller said:**
> System -> Preferences -> Sessions is the easiest way to have a program automatically start at login.

Thanks, sorted :D

---

