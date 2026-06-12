---
title: "How to get gdesklets working?"
date: 2004-11-10
forum: Desktop Environments
---

### Post by HiddenWolf on 2004-11-10
After a fresh install of gdesklets, I get the following error:

```
hidde@system:~ $ gdesklets
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
```

I want to be able to try some things, but the gdesklets deamons won't come up.

---

### Post by JProgrammer on 2004-11-10
That looks like a warning not an error. gDesklets should now be running. If you are talking about the gDesklets shell then it wont come up because version 0.26.2 that is in the repository doesn't have the shell. That was one of the major features to be introduced into 0.30 gDesklets is now at version 0.31.1 so you have to download and install from source if you want that.

---

### Post by Rancoras on 2004-11-10
Have you tried following the gdesklets howto?

[http://ubuntuforums.org/showthread.php?t=3012](http://ubuntuforums.org/showthread.php?t=3012)

---

### Post by kastorff on 2004-11-10
[QUOTE=Rancoras]Have you tried following the gdesklets howto?

[http://ubuntuforums.org/showthread.php?t=3012](http://ubuntuforums.org/showthread.php?t=3012)[/QUOTE]
 Or if you're adventuresome, install gDesklets 0.31.1 from Hoary.

*Sorry, my bad self posted that.*

---

### Post by ashley_v on 2004-11-10
I got the same error message.  Whatever it is it does not work.  I generally get this problem no matter what the distro with any prebuilt version of gdesklets.  I'm just going to install gdesklets from source, that pretty much solves it.

---

### Post by HiddenWolf on 2004-11-11
I have tried following man gdesklets.

Ie run gdesklets, then click a .display file. I just get an error saying nautilus does not know how to handle the .display file.

System management does not show any gdesklet process running either.

---

### Post by eKiNoX on 2004-12-13
Try editing "__init__.py"

sudo gedit /usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py

search for gtk.mainloop and replace it with gtk.main... 

Save the file and run desklets again.

---

### Post by jonah1980 on 2007-03-01
i just get this when i try running gdesklets under feisty amd64:

jonah@jonah-desktop:~$ gdeskletsStarting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

---

