---
title: "Weird problem with resolution on login"
date: 2005-04-28
forum: Desktop Environments
---

### Post by FeJaOr on 2005-04-28
I have a certain typo of screen resolution in the only account I have in this computer for Ubuntu 5.04 and the thing is that the login screen is at a certain resolution different than the one I have in my session...Is there any way to change the login resolution in order to match them??

---

### Post by heimo on 2005-04-28
I'm not sure. You could try to edit /etc/init.d/xorg.conf and remove all the other modes than the one you want. (Display-section, Modes-line) Somewhere under /etc/ is also configuration file for gdm (default graphical logon manager for Ubuntu/Gnome), which may have setting for resolution. Don't know.
[http://www.ubuntuforums.org/showpost.php?p=105064&postcount=1]("http://www.ubuntuforums.org/showpost.php?p=105064&postcount=1")

---

### Post by nad on 2005-04-28
The first suggestion was correct. If you were to edit (as the superuser) your /etc/X11/xorg.conf configuration file to order your available screen resolutions so that your requested resolution is the first in the list at your default display depth, the login screen will use this. Whew, that was a little technical. Look the file over and make a copy of the original file first so that if you mess it up you will be able to revert to a good working configuration. Post back with any questions or problems.

---

