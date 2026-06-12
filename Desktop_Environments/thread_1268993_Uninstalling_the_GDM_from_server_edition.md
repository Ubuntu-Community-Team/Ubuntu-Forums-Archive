---
title: "Uninstalling the GDM from server edition"
date: 2009-09-17
forum: Desktop Environments
---

### Post by RFXCasey on 2009-09-17
I've installed the gnome-desktop on my server and now want to remove it and all related packages completely, is this possible? Or do I have to reinstall the OS.

---

### Post by slakkie on 2009-09-17
You could remove them manually:

```

aptitude -D show ubuntu-desktop

```

This will show a depends section, which you can use to remove the packages and then it should be all gone.. 

There are some other methods to figure out these dependencies, so you could use that list directly in an aptitude remove command, but I forgot..

---

### Post by ajgreeny on 2009-09-17
You should be able to use ```
sudo apt-get remove gnome-desktop
``` Followed by ```
sudo apt-get remove --autoremove
```I think.  I have never used autoremove personally, but I think that is the command with the option you need to remove gnome-desktop and all its dependencies.

---

### Post by RFXCasey on 2009-09-18
Thanks, I'll try that, just hope I don't end up with a big mess on my hands. Oh well, if I do I will just have to reinstall which won't be too painful.

---

