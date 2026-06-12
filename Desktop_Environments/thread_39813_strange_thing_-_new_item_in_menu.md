---
title: "strange thing - new item in menu"
date: 2005-06-06
forum: Desktop Environments
---

### Post by waft on 2005-06-06
suddenly strange thing happend. new item "Debian" appeared in my applications menu.
why have it happened? I didn't do anything, I just installed nvidia driver and that should not influence applications menu

---

### Post by Martin Witte on 2005-06-06
I only know this menu in my Debian (sarge) installation. Do you have a Debian repository in your /etc/apt/sources.list?

---

### Post by waft on 2005-06-06
yes but it it was there long time before this happend. could nvidia-settings be from debian repository and cause this?

---

### Post by Triton on 2005-06-06
I saw this too!  I updated KDE to 3.4.1 and thats when I noticed the add menu item!   :?

---

### Post by cutOff on 2005-06-06
```
sudo apt-get remove menu menu-xdg
``` 
Hope this helps.

---

### Post by waft on 2005-06-07
[QUOTE=cutOff]```
sudo apt-get remove menu menu-xdg
``` 
Hope this helps.[/QUOTE]

I can't do that
```
The following packages will be REMOVED:
  k3b k3blibs kcontrol kdebase-bin kdelibs-bin kdelibs4 menu-xdg
```

---

### Post by simple on 2005-06-12
see here [http://ubuntuforums.org/showthread.php?t=25102&highlight=debian+menu+applications](http://ubuntuforums.org/showthread.php?t=25102&highlight=debian+menu+applications)
or
[http://ubuntuforums.org/showthread.php?t=19829&highlight=debian+menu+applications](http://ubuntuforums.org/showthread.php?t=19829&highlight=debian+menu+applications)
all thanks to search.
[http://ubuntuforums.org/search.php?searchid=931555](http://ubuntuforums.org/search.php?searchid=931555) <- your best friend

---

### Post by skoal on 2005-06-12
The name of the package which creates that menu is called "menu", as cutoff suggested.  Unfortunately, as you guessed might be the case, maybe k3b or another recently installed package had this as a dependency.  Why? Who knows...I'm still trying to figure out why just removing the "gam-server" package will in effect leave me with a completely useless tty console.

One possible sol'n: look at "man update-menus". I haven't tried this myself yet, since I prefer the extra menu, but there are several configuration files listed in those man pages, used to generate that menu.  You could simply delete those config files, or there may actually be an option in there to omit the menu from a certain DE or menu.

/edit - Just saw post above, and that sol'n seems to work.

\\//_

---

### Post by waft on 2005-06-23
thank you all

---

