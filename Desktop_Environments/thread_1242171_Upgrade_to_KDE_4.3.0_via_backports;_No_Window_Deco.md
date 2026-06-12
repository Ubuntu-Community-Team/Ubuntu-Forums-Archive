---
title: "Upgrade to KDE 4.3.0 via backports; No Window Decorations, Can't Type"
date: 2009-08-16
forum: Desktop Environments
---

### Post by _axiom_ on 2009-08-16
[COLOR="Red"]SOLVED: Hey kids, the trick is 'apt-get dist-upgrade' when adding new sources.[/COLOR]



I tried to upgrade my Jaunty box to KDE 4.3.0 by following the instructions on this page:

[http://www.kubuntu.org/news/kde-4.3](http://www.kubuntu.org/news/kde-4.3)

Now when I login to KDE, I have no window decoration, no wallpaper (it shows white and grey squares), and I can't type anything anywhere.  (Gnome is working fine.)

How can I get my KDE back?  

(Someone suggesting renaming the .kde folder, which I did, but that did not seem to work)

---

### Post by krazyd on 2009-08-16
If you follow the instructions linked below, you can backup your .kde folder to kde.tar. This will remove **all custom settings** for kde applications, so you will have to re-install themes etc, but it will return you to a working default kde 4.3 desktop. Also, you can copy anything you need from the backed-up kde.tar once you restart

[http://ubuntuforums.org/showthread.php?p=7745410#post7745410](http://ubuntuforums.org/showthread.php?p=7745410#post7745410)

---

### Post by _axiom_ on 2009-08-17
Yeah, I have already tried totally removing my user's .kde folders (and saving a backup of it).  I tried it again just now, but to no effect.  KDE still has no window decorations.

---

