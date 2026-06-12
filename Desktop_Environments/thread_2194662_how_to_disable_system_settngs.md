---
title: "how to disable system settngs"
date: 2013-12-19
forum: Desktop Environments
---

### Post by glenn_91 on 2013-12-19
Hello,

Would like to know how to disable system settings in my unity and also in the upper right corner panel..
My ubuntu is  12.04. I want this so that the people who use wouldn't be able to touch settings.

Thank you..

---

### Post by deadflowr on 2013-12-19
I wouldn't do it, but you could probably remove gnome-control-center, and gnome-control-center-unity.
Then the system settings wouldn't even be on the machine.

Of course, like I stated, I wouldn't do this.
And you really should wait on better advice.

Simply something you can ponder.

Edit: I thought it through and think the best thing would be to lock the screen and require a password so that if someone wants to use the machine and muck about they can either have you set up a user for them or use a guest session.
Why burden yourself and disable something you might want to use.

---

### Post by glenn_91 on 2013-12-19
thank you for quick response.. I was changed the permission of gnome-control-center to 700 and its work great.
I want to disable this because our employee if the admin are not in the computer they will edit the display, screen resolution, wallpaper etc.. that's why 
I really need to disable it.. thank you for the best idea you gave..

---

### Post by steeldriver on 2013-12-19
I think the "right' way to do this kind of thing is via dconf locks

[https://developer.gnome.org/dconf/unstable/dconf-overview.html](https://developer.gnome.org/dconf/unstable/dconf-overview.html)

---

