---
title: "Disable .Trash-directory for certain mounts"
date: 2007-05-20
forum: Desktop Environments
---

### Post by toxicavenger on 2007-05-20
Ubuntu creates these annoying .Trash-<username> folders on the USB-drives and smbfs volumes that I mount. I  want to configure ubuntu to quit doing this. How would I go about?

I mean, I could create a crontab job that deletes these directories every 60 seconds, but that does not strike me as an elegant solution. Surely the best way is instead to have ubuntu quit creating these ugly folders (for some volumes that I specify)....

---

### Post by SomeGayDude on 2007-05-20
I agree.  Is there a way to keep ubuntu from adding a .trash folder to removable disks?  It would make life a lot easier.  Thanks

---

### Post by aysiu on 2007-05-20
In Thunar, I created a Custom Action for this command: ```
mv %N ~/.local/share/Trash/files/
```

---

