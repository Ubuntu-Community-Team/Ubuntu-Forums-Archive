---
title: "Kmenu icon goes generic"
date: 2008-06-13
forum: Desktop Environments
---

### Post by portlandor on 2008-06-13
Hi, 

I started a similar thread, but I can't find it.  Somehow my Kmenu icon turned into a generic one.  its not such a big deal, but I hate it when I don't know what I did.  This is the one icon on the task bar which doesn't have a config setting.  How do I get it back?

Thanks,  Rob.

---

### Post by aysiu on 2008-06-13
I don't know. But we can probably diagnose the problem better if you create and log in as a test user. If the test user has a generic icon, we know it's a system-wide problem. If the test user has the regular icon, we know it's a user-specific problem.

By the way, can you attach a screenshot of what "generic" looks like?

---

### Post by portlandor on 2008-06-14
OK, 

I've attached the icon jpeg.  However, I don't know how to create an account and/or login as a test user.  I will ask on the beginners forum

Rob

---

### Post by BlackDragonBE on 2008-06-14
/home/YOURNAME/.kde/share/icons/CURRENTTHEME/128x128/apps/go_kde.png
I think that's what u need to change.

---

### Post by Tony Sivori on 2008-06-14
> **portlandor said:**
> Hi, 

I started a similar thread, but I can't find it.  Somehow my Kmenu icon turned into a generic one.  its not such a big deal, but I hate it when I don't know what I did.  This is the one icon on the task bar which doesn't have a config setting.  How do I get it back?

Thanks,  Rob.

I prefer the old amber K icon instead of the new blue K start icon, so I too had to find its location. Here is the location of my K start button (Kubuntu 8.04 running KDE 3.5, not KDE 4.x):

/usr/share/icons/default.kde/32x32/apps

file name is kmenu.png

I've attached the original blue icon.

Looks like the attchment did not go through.

---

### Post by portlandor on 2008-06-20
Hi,

That /home/rob/.kde/share/icons... etc doesn't even exist in my home directory.  I tried to create it and add the icon file but nothing happened.

Rob.

---

