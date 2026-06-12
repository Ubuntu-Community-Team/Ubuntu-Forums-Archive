---
title: "uninstalled XGL, but now can't start up ubuntu"
date: 2006-12-09
forum: Desktop Environments
---

### Post by corevette on 2006-12-09
So originally, I wanted to try compiz and i installed xgl in the process, but later realized my video card wouldn't do that well with it so i uninstalled compiz.  now i want to uninstall xgl and so i did, but after i restarted, it says there was an error saying something like 'GDM: Xserver could not find XGL.'  so i went into recovery mode and here i am.  heres my GDM.conf file: [http://paste.ubuntu-nl.org/36106/](http://paste.ubuntu-nl.org/36106/) .  I believe that after i uninstalled XGL, it didn't tell GDM that i did, and so when it starts up, it's looking for XGL; but thats what i'm thinking.  any help please?

---

### Post by scrooge_74 on 2006-12-09
> **corevette said:**
> So originally, I wanted to try compiz and i installed xgl in the process, but later realized my video card wouldn't do that well with it so i uninstalled compiz.  now i want to uninstall xgl and so i did, but after i restarted, it says there was an error saying something like 'GDM: Xserver could not find XGL.'  so i went into recovery mode and here i am.  heres my GDM.conf file: [http://paste.ubuntu-nl.org/36106/](http://paste.ubuntu-nl.org/36106/) .  I believe that after i uninstalled XGL, it didn't tell GDM that i did, and so when it starts up, it's looking for XGL; but thats what i'm thinking.  any help please?

Did you then installed gnome to have a desktop?

---

### Post by corevette on 2006-12-09
i'm not understanding what you are saying

---

### Post by scrooge_74 on 2006-12-10
Maybe this will help

[http://ubuntuforums.org/showthread.php?t=127090&highlight=xgl](http://ubuntuforums.org/showthread.php?t=127090&highlight=xgl)

---

### Post by corevette on 2006-12-10
i don't need help installing it, i need help getting rid of xgl.  i tried uninstalling it, but it had errors in the xserver once i restarted the computer so i was forced to reinstall it under recovery mode.

---

### Post by corevette on 2006-12-14
i got rid of xgl, so my problem is fixed, all i needed to do was to delete a few lines of code in the xorg file i put in before

---

