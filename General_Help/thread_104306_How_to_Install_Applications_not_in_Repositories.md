---
title: "How to Install Applications not in Repositories"
date: 2005-12-15
forum: General Help
---

### Post by Noah0504 on 2005-12-15
There are certain applications I would like to install that are not available in the repositories.  Rhythmbox 0.92 is one of these applications.  Many offer compiled packages, but I was wondering if there is anything special that needs to be done before it is installed.  Will it automatically replace the current version, or will it list both versions?

---

### Post by adwait on 2005-12-15
Well download the .deb file and run
```
sudo dpkg -i <file.deb>
```

You will have to be careful about the dependencies though.

---

### Post by Noah0504 on 2005-12-15
Well, I know how to install a .deb package, but I don't want to end up having two versions of the same application sitting in my menus.

---

### Post by RAOF on 2005-12-15
The new deb **should** replace the existing Rhythmbox.  If it doesn't just remove the old one from synaptic.

---

### Post by Noah0504 on 2005-12-15
Thanks for the help.  :)

---

### Post by imrumpf on 2005-12-15
I would also keep an eye out for **gdebi**. It is being developed for Dapper Drake and basically it is a visual .deb file installer. No more command line! :D Don't think it works with Breezy (too many dependancies) but keep an eye out for it soon.

---

### Post by Noah0504 on 2005-12-15
That will really make things easier for noobs like me.

---

### Post by imrumpf on 2005-12-15
not only noobs, people like me (I call myself a moderate ubuntuer) who just don't want to have to hastle around. Imagine: being in firefox, seeing a program you like, using the "OpenDownload" extension to click on the .deb link and selecting Run, and off it installs. Windows users should come flocking to us now :p

---

### Post by Sp@z on 2005-12-15
On my knees praying "Dear God let this be  true, windows is evil, let it be true"

(In case you can't tell Linux has bitch slapped me and making me earn my keep here.)

---

### Post by imrumpf on 2005-12-15
Prayers answered, it IS true!

If you don't want to wait the 4 months till Dapper, there is another program called [**Debins**]("http://programmer-art.org/debins") that will do something quite similar right now in Breezy. Not sure if it checks and tries to fulfill dependancies like gdebi should when released, but it's a start.

---

