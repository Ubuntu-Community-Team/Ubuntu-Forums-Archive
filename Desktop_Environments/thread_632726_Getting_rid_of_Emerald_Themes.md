---
title: "Getting rid of Emerald Themes"
date: 2007-12-05
forum: Desktop Environments
---

### Post by Aeroice on 2007-12-05
Just a slight question...

How do you remove emerald themes, for heavens sake?

And I mean, literally, the application. So I can switch back to regular ubuntu theming.

---

### Post by Cresho on 2008-01-20
If you are running gutsy, I just uninstalled the two items that are related to emerald when you search for it in synaptic installer.

they are:
emerald
libemeraldengine0

---

### Post by rosegarden78 on 2008-01-20
Are you using latest distro?  Compiz was recently integrated into Beryl as of Gutsy.  If you are using Feisty or 6-month old kernels it's time to backup your /home folder and clean install Ubuntu.  Then add kdm and xfce as you like it.  There is now a simple switch under Change Desktop that turns these effects on and off.  And of course you can choose any normal theme like Plastik or Human.

You may also try this at the terminal:

sudo aptitude purge beryl
sudo aptitude purge compiz

Otherwise backup and clean install latest distro.

---

### Post by rosegarden78 on 2008-01-23
It interesting I just tried compiz and avant dock in Xubuntu it works perfectly.
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

