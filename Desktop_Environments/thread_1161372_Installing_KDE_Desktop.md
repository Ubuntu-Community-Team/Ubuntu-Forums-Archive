---
title: "Installing KDE Desktop"
date: 2009-05-16
forum: Desktop Environments
---

### Post by qjmoss on 2009-05-16
I would like to install KDE 4.3 Beta 1.

First-

Is this possible.. I'm not sure if it is released, I want the latest version of KDE out.

Is there a way to keep the KDE applications separate from my Gnome desktop.


And, is there now an easy way to completely remove the KDE desktop when i'm done with it, I know before it was pretty difficult to remove it. sudo apt-get remove kde-desktop didnt remove all the packages.

---

### Post by goldblattster on 2009-05-16
I don't have much to say about KDE 4.2 beta 1, but I believe installing kubuntu-desktop using aptitude and then remove it using aptitude will get rid of all those extra packages, but i am not completely sure, so you might want to check.

---

### Post by benerivo on 2009-05-16
To get a beta version of kde 4.3 on ubuntu, you'll need to use a separate repository. These are typically ppa repositories. Check this thread for some 4.3 repositories...
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1150657](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1150657)
You can't really isolate gnome and kde installations, but i would create a new user account, to try out kde. To uninstall kde completely, just get rid of all packages with kde or qt in their name. Not a one-stop uninstall process, but it will do the job,

---

### Post by qjmoss on 2009-05-18
Well maybe I just want the newest version of KDE out.. No beta for me


What would the command be, just sudo apt-get install kde-desktop? and is it a separate rep?

---

### Post by DLG102282 on 2009-05-18
sudo apt-get install kubuntu-desktop. It isn't a seperate repo.

---

### Post by qjmoss on 2009-05-18
Thank you

---

