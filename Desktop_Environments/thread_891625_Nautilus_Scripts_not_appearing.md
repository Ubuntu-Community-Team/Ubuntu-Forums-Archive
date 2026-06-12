---
title: "Nautilus Scripts not appearing"
date: 2008-08-16
forum: Desktop Environments
---

### Post by retrodans on 2008-08-16
I am trying to get the nautilus-script for svn working on my computer.  Sadly, I thought I had installed everything, but when I right click on a file, there is no scripts option.:confused:

Is there a setting I am supposed to activate or something before this works?  I don't think I am missing anything, as the svn script was installed through the package manager, and it normall suggests if other packages need to be installed.

Thankyou for any light you can shed
Dan

---

### Post by kaibob on 2008-08-16
I'm not familiar with the SVN Nautilus script, but the following thread (which is old) may be of help:

[http://ubuntuforums.org/showthread.php?t=229178](http://ubuntuforums.org/showthread.php?t=229178)

---

### Post by retrodans on 2008-08-16
Thankyou ever so much, I did search the forums, but apparently not thoroughly enough.  If you are interested the package I installed for this was:
nautilus-script-collection-svn
It's on the package manager.  Then all I needed to do was copy the files it created into the correct folder using:
sudo mv /usr/share/nautilus-scripts/Subversion $HOME/.gnome2/nautilus-scripts/

It seems any scripts installed through the package manager put in this folder, so all need to be copied across.

Thankyou again
Dan:)

---

