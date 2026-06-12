---
title: "Wine doesn't work after upgrade to Lucid"
date: 2010-05-07
forum: Desktop Environments
---

### Post by someitalian123 on 2010-05-07
When I try to run exes nothings happens. Anyone know what to do?

---

### Post by jbrown96 on 2010-05-07
KDE probably doesn't know how to handle exes after the upgrade. Try reinstalling wine. ```
sudo apt-get install wine1.2
```

---

### Post by someitalian123 on 2010-05-07
I already uninstalled and reinstalled it. Wine Windows Program Loader shows up on the bottom panel when I click on an exe and nothing happens.

---

### Post by someitalian123 on 2010-05-07
Ok. I tried running the exe from the terminal and it worked. This is good news for me but why doesn't it when I try to click on it.

---

### Post by Zorael on 2010-05-08
Try (temporarily) renaming your **~/.local/share/applications** directory, then run **kbuildsycoca4** and see if it behaves after that.
```
$ cd ~/.local/share
$ mv applications applications.backup
$ kbuildsycoca4
```

Files in there are user-specific settings that override the system-wide (and default) files in **/usr/share/applications**. Those files define your installed desktop applications, listing their names, descriptions and comments, as well as listing the file extensions and mimetypes that they can and should handle. Perhaps your have local user settings left from before the upgrade that override new behavior in lucid.

---

### Post by Kalom on 2010-06-08
Hi all I have exactly the same problem. I tried the above (kbuildsycoca4), purging and reinstalling, and the situation is still the same: through shell, the program opens, through clicking on the .exe in the dolphin window, it starts trying to open for a few seconds but nothing seems to happen after that.

worked ok 4 days ago, yesterday I upgraded to Lucid, and today, no .exe-clicking.

Not too worried since it works, but it's highly uncomfortable.

---

