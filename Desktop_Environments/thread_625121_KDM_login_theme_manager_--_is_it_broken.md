---
title: "KDM login theme manager -- is it broken?"
date: 2007-11-27
forum: Desktop Environments
---

### Post by p_quarles on 2007-11-27
I haven't seen this mentioned anywhere, but I haven't been able to get the KDM login theme manager to work since upgrading to 7.10. I can get it to use a theme from the repositories, but it simply won't load any themes from KDE-look. I even tried setting a path to the theme in kdmrc, but that resulted in an error message at login: "cannot parse theme in /path/to/file."

Anyone having the same problem? Any solutions?

---

### Post by p_quarles on 2007-11-28
Bump. 

I'm going to file a bug report on this later today, so if anyone can just confirm the problem, that would be helpful to me.

---

### Post by madscientist159 on 2007-11-28
I have the exact same problem on a stock install of Gutsy and Kubuntu--I am executing an update right now to see if the issue will go away or not.

My guess is that both the theme manager plugin and KDM are currently broken with regards to themes.

Tim

---

### Post by Melcar on 2007-11-28
I don't think it's broken.  Mine recently got updated and now whenever I lunch it, it complains about some master file that is overwriting the theme settings.

---

### Post by loboc on 2008-02-04
Same Errors. KdmTheme is way broken in that it wont install themes form kde-look.

Manual Install of the theme results in the same parse error.   

Bug mentioned by developer here 

[http://www.kde-apps.org/content/show.php?content=22120]("http://http://www.kde-apps.org/content/show.php?content=22120")

Changelog:

 2007-09-28 (1.2): Backport of the KDE4 version
 2007-10-08 (1.2.1): Fixed a porting bug where the selectionChanged() signal was never  
 connected correctly.
 [B]2007-12-16 (1.2.2): Actually save things... (I am quite embarrassed about this one..)
 Enable saving when you only disable themes. (emit the changed signal)[/B]

Perhaps this hasnt made it back to 3.5 from upstream because attention being focused on kde4

---

