---
title: "getting a java application to show up in &quot;open with&quot; list"
date: 2013-07-17
forum: Desktop Environments
---

### Post by gleedadswell on 2013-07-17
Hi everyone,

I'm running Maple (a symbolic algebra program for those who don't know it) under Ubuntu 12.04.  One of my frequent complaints about Maple is that, while they provide a linux version, it is very poorly integrated with linux.  So, they don't provide it as .deb and .rpm files.  They have their own custom built installer which doesn't do nearly such a good job of setting everything up.  Fundamentally Maple is just a rather big and complicated java application.

Anyway, I was able to make maple come up in dash fairly easily (using alacarte).  The installer also created a .desktop file which I was able to drag to my launcher.  But it took me a while to get maple to show up in the "open with" list in nautilus so that I can set it as the default application for all of my maple files.  So I thought I'd post the solution in case it is useful to other people.  This issue may come up with other applications (particularly java applications which people often install without going through the package managers).

Go to the .desktop file and added %f to the "Exec=..." line as suggested here:

[http://ubuntugenius.wordpress.com/2012/06/18/ubuntu-fix-add-program-to-list-of-applications-in-open-with-when-right-clicking-files-in-nautilus/](http://ubuntugenius.wordpress.com/2012/06/18/ubuntu-fix-add-program-to-list-of-applications-in-open-with-when-right-clicking-files-in-nautilus/)

If that doesn't work try %U instead of %f (can someone who knows about .desktop files explain what these codes mean?).  At the point I had done this it still wasn't working.

The problem was that the maple installer had created this .desktop file in the directory where I had told it to install maple.  In my case it was in

/usr/share/maple17/bin

because I had told it to install maple to /usr/share/maple17.  But for nautilus to see the .desktop file it needs to be in

/usr/share/applications

So I copied it to that location and now everything seems to work.

Cheers!

---

### Post by theDaveTheRave on 2013-07-18
gleedadswell,

there is a third location for 'desktop files this is the

```

~home/.local/share/applications

```

you can use this for user specific settings, such as setting language, on a per user bases.

you may also prefere to creat a link between your main .desktop file in the /usr/share/maple17/bin and the desktop file in /usr/share/application this will ensure that any modification to either file will only need to be done once, something like
```

ls /usr/share/maple17/bin/.desktop /usr/share/applications/maple.dekstop

```

you will need to check if you want to use hard or soft links

David

---

