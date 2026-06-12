---
title: "QT Themed apps look horrible in Ubuntu - finding no solutions"
date: 2010-08-22
forum: Desktop Environments
---

### Post by david.rahrer on 2010-08-22
I'm on a freshly installed (two months ago) Ubuntu Lucid 10.04 desktop and just noticed that QT themed apps like Netbootin and Luckybackup look awful on my system, like they did years ago before the theming was straightened out.  So I installed a clean version of Lucid 10.04.1 on a vbox virtual machine and the same apps look fine, well-integrated into the Gnome look and feel.  I set it up with the same Radiance theme I am using on my main system.  You can see the attached images for comparison.

My searches are coming up essentially empty.  I did figure to install qt4-qtconfig and ran it.  It looked fine and the setting appeared exactly as they do on the test VM (see attached image).  Aside from running Compiz, I can't think of anything else I've done that may affect the look.  

Has anyone a clue about this?  I'm tempted to start over from scratch since a new install seems to work, but that would take a lot of hours to recreate, and surely there are some settings I could check.  Any guidance would be greatly appreciated!

PS: If there is a more appropriate forum for this post, please let me know.  I didn't have much to go on.

Thanks,

---

### Post by david.rahrer on 2010-08-23
I finally figured it out.  Both UNetbootin and LuckyBackup run in superuser/root by default.  I ran 'gksudo qtconfig' and set it the theme for GTK+, saved and they both look fine now.  I'm not sure why my fresh install of Lucid 10.04.1 worked out of the box on that but this fixed it.  Hope that saves someone else some time and frustration.

---

