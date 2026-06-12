---
title: "Trying to instal a login screen but not working?"
date: 2006-01-05
forum: Desktop Environments
---

### Post by kubuntu32 on 2006-01-05
~/.kde/share/apps/kdm/themes

That is where I should be extracting the files correct?  So i'm not exactly sure where that is so I used the search function and it found that folder.  Unfortunately that folder is read-only.  I never created a root user or password and I definately don't know how to change its permission.  Not exactly sure if this is the case, and I don't want to go further without knowing exactly what the problem is just in case I mess up.

Help a linux noob out please?  What am I doing wrong?

---

### Post by adwait on 2006-01-06
You need to modify a bunch of files to change the KDM theme, try this: 
[http://www.kde-apps.org/content/show.php?content=22120&forummode=2&forumpage=10&forumexplevel=0](http://www.kde-apps.org/content/show.php?content=22120&forummode=2&forumpage=10&forumexplevel=0)

---

### Post by sharke on 2006-01-06
[QUOTE=kubuntu32]~/.kde/share/apps/kdm/themes

That is where I should be extracting the files correct?  So i'm not exactly sure where that is so I used the search function and it found that folder.  Unfortunately that folder is read-only.  I never created a root user or password and I definately don't know how to change its permission.  Not exactly sure if this is the case, and I don't want to go further without knowing exactly what the problem is just in case I mess up.

Help a linux noob out please?  What am I doing wrong?[/QUOTE]
The file your looking for is in your home directory .kde//share/apps/ksplash/Themes
In konqureor you have to check hidden files in the view mrnu to see it.
Regards
Sharke

---

