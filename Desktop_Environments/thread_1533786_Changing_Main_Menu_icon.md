---
title: "Changing Main Menu icon"
date: 2010-07-18
forum: Desktop Environments
---

### Post by johnskoric on 2010-07-18
Hi!
I have problem.
I want to change this icon, i do it right, but it stays just for one user, not for all users!
How to change it for everyone?
Thanks for answers!!
And yep, sorry for bad English I´m from Croatia!;)

---

### Post by hhh on 2010-07-18
Here's one way...
[http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/](http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/)

Here's another...
[http://simplistictechnologies.com/blog/2009/06/ubuntu-change-menu-icon/](http://simplistictechnologies.com/blog/2009/06/ubuntu-change-menu-icon/)

---

### Post by johnskoric on 2010-07-19
> **hhh said:**
> Here's one way...
[http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/](http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/)

Here's another...
[http://simplistictechnologies.com/blog/2009/06/ubuntu-change-menu-icon/](http://simplistictechnologies.com/blog/2009/06/ubuntu-change-menu-icon/)

Yep, but i try all two ways, but, when i create new user, main menu icon is normal, Ubuntu :(

---

### Post by TheWeakSleep on 2010-07-19
The menu icon is determined by the icon set that you are using, so if you were to change the icon set, it would change the menu icon. to change the menu icon for all users, they have to be using the same icon set. for instance, if you were to navigate to /usr/share/icons/ubuntu-mono-dark, and find the icon named "start-here.svg" and replace it with your own icon, that would change the icon for any users using the icon set ubuntu-mono-dark, but if they changed there theme to one that uses ubuntu-mono-light, it would be the dark version of the ubuntu logo.

hope that clears some stuff up :)

---

