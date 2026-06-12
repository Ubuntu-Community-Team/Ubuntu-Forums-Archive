---
title: "Default gconf and dconf for all Users"
date: 2012-11-07
forum: Desktop Environments
---

### Post by tvarwigsoftware on 2012-11-07
I am trying to find a way to set the default gconf and dconf settings for all users. I know in the /usr/share/glib-2.0/schemas has xml files for the settings. I Changed the settings in the xml files with root and created a new user and the settings did not transfer. Under /etc/skel does not have any local user settings. I want default gtk theme, fonts for all users. How can i do that?

I am using 12.04.1

---

### Post by critin on 2012-11-07
I may not be understanding what you want to do, if so--sorry.  But other users have their own separate system.  They will run the default until they change it.  You can share docs, files, folders, etc., but settings?  I don't think so, but if I'm wrong I'm learning something too.

---

### Post by ragtag on 2013-04-24
For new users, you could in theory save the changes to /etc/skel/   This gets copied to new users home folder when they are created.

For existing users, I'm not so sure.

---

