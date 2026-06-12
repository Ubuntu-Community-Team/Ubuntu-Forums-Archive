---
title: "Can't downgrade Beryl"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by mattigus on 2007-05-04
I can't use beryl unless I downgrade Beryl to version 0.2.0.  For some reason I can't do this through the package manager.  Can anybody help me?

Sorry if this is a double post.  I posted this, but can't find it for some reason.

---

### Post by Belyel on 2007-05-04
are you using beryl from the SVN repository?  The best/only surefire way to revert your beryl to an older version is to completely remove beryl and emerald, change your repositories, then install again.  The easiest way is to type

```
sudo apt-get remove --purge beryl beryl-* emerald emerald* libberyl* libemerald*
```

This command will completely remove and purge beryl and emerald, their libraries, and their settings.  To make sure you got everything, you can also remove the .beryl and .emerald folders in your home directory, although I'm not sure that's necessary.  Oh, and make sure you are logged into a normal gnome session or on the failsafe terminal, or you won't be able to completely remove beryl.

After you've removed beryl, restart X (ctrl-alt-backspace), make sure you are using the standard beryl repository (not trevino's SVN repo) and install it fresh.  Good luck!

---

