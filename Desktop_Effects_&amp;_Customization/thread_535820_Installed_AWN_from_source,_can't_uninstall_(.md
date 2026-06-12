---
title: "Installed AWN from source, can't uninstall :("
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-08-27
AWN works nicely, and i remember the preferences window working, but somewhere along the line the preferences window decided to stop opening:
```

Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 97, in __init__
    self.launchManager = awnLauncher(self.wTree, self.AWN_CONFIG_DIR)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnLauncher.py", line 66, in __init__
    self.make_model()
  File "/usr/local/share/avant-window-navigator/awn-manager/awnLauncher.py", line 124, in make_model
    self.refresh_tree(uris)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnLauncher.py", line 134, in refresh_tree
    self.model.set_value (row, 0, self.make_icon (i))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnLauncher.py", line 168, in make_icon
    if "/" in name:
TypeError: argument of type 'NoneType' is not iterable


```

so i found another thread that recommended uninstalling and getting it from the repos. 

I installed from source, and i deleted teh source. I tried redownloading it and running "sudo make uninstall", but that didnt work.


How do i delete AWN (or anything really) that was installed from source if the make file doesn't have the capability or if you dont have the makefile? just search for all the relevant files and delete?

---

### Post by cilynx on 2007-08-27
look into 'checkinstall'.  It takes your normal "./configure && make && make install", watches what it does, then makes a deb package.  You can then uninstall the deb package you just made.

---

### Post by Dark Star on 2007-08-27
To uninstall AWN open synaptic search Avant Windows Manager or Avant right click on the displayed AWN enry mark for complete removal .. if this fails re-install it and try un-installing it :)

---

### Post by superyounan1 on 2007-08-27
well i reset AWN's settings by doing this
```

gconftool-2 --recursive-unset /apps/avant-window-navigator

```

and i was able to open the preferences window, but AWN is just way too finiky for me! Everyone reports it as the best dock out there, but it gives me plenty of problems:

-randomly the preferences menu stops working
-draging launchers onto the dock, those launchers dont appear int he preferences launchers tab
-add lauchers through preferences, nothing happens. Restart AWN, and all launchers vanish!
-cant rearrange launchers

am i the only one that just cant get it to behave?

btw i reinstalled it from source and uninstalled it, then installed from teh repos. Thanks

---

### Post by specialk4urmind on 2007-11-29
> **Dark Star said:**
> To uninstall AWN open synaptic search Avant Windows Manager or Avant right click on the displayed AWN enry mark for complete removal .. if this fails re-install it and try un-installing it :)

my AWN's not listed in synaptic nor in add/remove programs.  I'm super noob at ubuntu so I need help uninstalling this thing.  I don't even know how I got it to install in the first place but I don't like it and want it unstalled.  Help please!

---

