---
title: "Ugly Opera"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-08
Ok, I just don't understand why, but Opera looks really ugly under gnome - even compared to firefox and other applications.

The main body of opera looks great, and can be themed as I like and looks nice whichever theme I use.  However, the menus and pop-ups that it spawns are ugly,  I am sure that it is not supposed to be like this.

What should I be doing here?

My Opera version info:

Version
9.00 Internal
Build
300
Platform
Linux
System
i686, 2.6.15-23-386
Qt library
3.3.5
Java
Java Runtime Environment installed

---

### Post by Vytas on 2006-06-08
As far as I know, Opera uses qt, so you need to change qt theme. Try searching ubuntu forums and wikis, I think this HOWTO might be helpful [http://ubuntuforums.org/showthread.php?t=56630](http://ubuntuforums.org/showthread.php?t=56630)

However, I don't even have qt installed :)

---

### Post by Lunar_Lamp on 2006-06-08
I followed the guide, and it's still the same :-(

It has affected other programs, for example amarok, but not Opera.

---

### Post by Case_f on 2006-06-08
You're most likely using static version of Opera, which does not have antialiasing enabled for menus and popups (hence the ugliness). Try downloading the shared package.

---

### Post by Lunar_Lamp on 2006-06-08
I was using the static version I believe, but how do I uninstall it, keep my bookmarks etc, and install the shared version?

I tried just installing the shared version, and whilst there appeared to be no error, the fonts are still unaliased - i.e. the static version is still the one loaded.

---

### Post by alnilam on 2006-07-20
Try starting Opera with the command "opera --style default". This made my Opera look much better. If it works you can edit your starter and always use this command for starting opera.

---

### Post by sanguinemoon on 2006-07-24
I have the same problem, with the static and shared versions :( The opera --style default doesn't solve it here.

I've tried everything that I know. I removed the .opera directory. I've deleted the /lib/opera directory. Tried static and shared versions, even went back down to 8.54 (because I remember Opera not looking this bad in Linx, so I guessed incorrectly  maybe it was an Opera 9 bug)

---

