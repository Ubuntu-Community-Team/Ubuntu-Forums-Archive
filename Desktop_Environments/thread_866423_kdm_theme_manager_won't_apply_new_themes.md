---
title: "kdm theme manager won't apply new themes"
date: 2008-07-21
forum: Desktop Environments
---

### Post by Bosonator on 2008-07-21
Hiya,

At my KDE login screen, I used to have the nice variant on the default kubuntu theme (called "Kubuntu O2 - No Userlist"). Upon upgrading to Hardy, it no longer displays that theme. If I have "kde-kdm-themes" installed, I can use the login themes included in that package, but nothing else seems to work. Any fixes? Thx!

---

### Post by Sword2 on 2008-07-29
make sure that you have Wallpaper=default_blue.jpg line in the /etc/kde3/kdm/backgroundrc file and in same path you have the file kdmrc with the following lines under the [X-*-Greeter] section:
Theme=@@@ToBeReplacedByDesktopBase@@@
UseTheme=true

After that reboot.

Then you can use the Theme manager to change themes.  If you use the login manager to change the background (wallpaper) to something else than what it's set to you will mess it up again.  Yes, they messed that up since Feisty and havent fixed it since.

Enjoy.:)

---

### Post by tim71 on 2008-08-30
> **Bosonator said:**
> Hiya,

At my KDE login screen, I used to have the nice variant on the default kubuntu theme (called "Kubuntu O2 - No Userlist"). Upon upgrading to Hardy, it no longer displays that theme. If I have "kde-kdm-themes" installed, I can use the login themes included in that package, but nothing else seems to work. Any fixes? Thx!

It seems that KDM theme manager has a supid bug that causes the theme path to be written into /etc/kde3/kdm/kdmrc inside a quotation marks - 
like this
```
Theme="/usr/share/apps/kdm/themes/skyline"
```

when it supposed to be like this
```
Theme=/usr/share/apps/kdm/themes/skyline
```

If this path defined with quotation marks, KDM displays error message
```
Cannot open theme file "/usr/share/apps/kdm/themes/skyline"
```

Someone could post a bug or something.

Until it's fixed the easyest way is to edit kdmrc manually...

---

### Post by ChompTheMan on 2008-08-30
I reported this a while ago:  [https://bugs.launchpad.net/ubuntu/+source/kdmtheme/+bug/222754](https://bugs.launchpad.net/ubuntu/+source/kdmtheme/+bug/222754)

---

