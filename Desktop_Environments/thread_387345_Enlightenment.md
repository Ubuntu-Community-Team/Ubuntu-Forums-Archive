---
title: "Enlightenment"
date: 2007-03-18
forum: Desktop Environments
---

### Post by epikinon on 2007-03-18
Can anybody give some instructions as to what I need to do to install enligthenment. I'm very new to Linux and I don't understand dependancies and how to go about installing it. Thank you

---

### Post by kanha on 2007-03-18
open your terminal
accessaries---->terminal
type
sudo apt-get install enlightenment

after installation logout and at login screen choose session type as enlightenment,login
:guitar:

---

### Post by Kobalt on 2007-03-18
> **kanha said:**
> 
sudo apt-get install enlightenment

Just in case you want to uninstall enlightenment afterwards you'd rather use aptitude instead of apt-get, it manages dependencies removal better.
```
sudo aptitude install enlightenment
```
Here is a guide on how to install the latest version by the way : 
[http://www.ubuntuforums.org/showthread.php?t=319336](http://www.ubuntuforums.org/showthread.php?t=319336)

Cheerio !

---

### Post by ynnhoj on 2007-03-18
> **Kobalt said:**
> Here is a guide on how to install the latest version by the way : 
[http://www.ubuntuforums.org/showthread.php?t=319336](http://www.ubuntuforums.org/showthread.php?t=319336)that's how i'd do it; just keep in mind that enlightenment dr17 isn't quite perfect yet :).  but if i remember correctly, i had better luck with e17 than i did with the version that is in the ubuntu repositories..

---

### Post by Kobalt on 2007-03-18
> **ynnhoj said:**
>  i had better luck with e17 than i did with the version that is in the ubuntu repositories..
Clearly :)

---

### Post by outofnicks on 2007-03-21
Pardon me for hijacking this thread, but it may help the original poster.
 I just installed Enlightenment (which was easy with the package manager) but I can't do anything with it. No application menu whatsoever! How do I open something? Firefox, a file manager, anything? I spent about an hour looking at the help documentation, to no avail. 
I like Enlightenment, it's very cool but where's it's functionality?

---

### Post by yabbadabbadont on 2007-03-21
Try right or left-clicking on the desktop for a menu.

---

### Post by outofnicks on 2007-03-21
Well, I did try every manner of right-, left- and middle clicking but all I saw were configuration and settings menus. Now after logging out and back in again I have the User menu, or I should say menus--a seperate one for KDE, Gnome, and "Other" which should be for xfce4, and then Enlightenment Epplets which is empty. 
At least I've got the ball rolling now :)  But I have some customizing to do! 
Thanks.

---

### Post by cmichaelboyd on 2007-03-21
You may also consider installing "menu" and "menu-xdg".  These two packages will give you a "Debian" menu that has pretty much all of your software already in it and separated into different catagories.  Then, whenever you install new software, you can just go to a terminal and type "update-menus" and it should add it it.

Good Luck

Chris

---

