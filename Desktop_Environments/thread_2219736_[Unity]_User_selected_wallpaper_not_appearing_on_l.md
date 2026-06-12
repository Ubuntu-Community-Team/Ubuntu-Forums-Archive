---
title: "[Unity] User selected wallpaper not appearing on login"
date: 2014-04-25
forum: Desktop Environments
---

### Post by Mcgloud on 2014-04-25
Hello dear users,

I remember in older version of Ubuntu that when a users selects his own wallpaper it gets added to the user´s profile and it would appear on the Unity login screen.
This feature, however, is disabled by default in 14.04. I´ve tried dconf-editor to select my wallpaper manually but it didn´t work.

Anyone got a work-around for this?

---

### Post by kostkon on 2014-04-25
The wallpaper should be in your Pictures folder and you should change the permissions for that folder so that it is accessible to the Others group (right click on the folder, select Properties, then Permissions and change it from there.)

Hope that helps.

---

### Post by deadflowr on 2014-04-25
As stated it has to be in your Pictures folder directly, and not a sub-folder of Pictures.
From what I've noticed.

---

### Post by mcduck on 2014-04-28
> **deadflowr said:**
> As stated it has to be in your Pictures folder directly, and not a sub-folder of Pictures.
From what I've noticed.

I always keep my wallpapers in a subfolder (~/Pictures/Wallpapers") and they work just fine for lightdm. Having the read permission is still required, or course.

---

### Post by CharlesJohnston3 on 2014-04-28
It also may be that you have the file on another drive that for some reason boots up AFTER you login.
Thus your normal desktop looks fine, but when you cold boot/restart, you get the default background, then login and poof its there.

EX: Coolwallpaper.jpg on a USB Drive (Can be a secound hard drive at times)
When you boot up, the drive isnt mounted yet, and you get Default wallpaper. Then you login, and wow theres Coolwallpaper.jpg as your wallpaper.
To fix, just copy the wallpaper to somewhere under pictures, then set it as your wallpaper.

This oopsie, has caught me a few times too. ;)

---

