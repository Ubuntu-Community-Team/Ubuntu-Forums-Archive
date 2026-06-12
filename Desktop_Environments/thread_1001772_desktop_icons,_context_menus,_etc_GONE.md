---
title: "desktop icons, context menus, etc GONE"
date: 2008-12-04
forum: Desktop Environments
---

### Post by Apocrathia on 2008-12-04
they're just gone. if I open terminal and type "nautilus restart" everything reappears and works, until I close the terminal. I've tried reinstalling the nautilus package but it didn't really fix anything. any ideas?

---

### Post by Shwefty on 2008-12-04
Maybe put "nautilus restart" into your Sessions for startup?  This'll get around that open Terminal window thing if it works.

---

### Post by Apocrathia on 2008-12-04
actually I just did that before I refreshed the thread to see if there were any replies. it works, however I get a little error message. a little annoying but everything works again. hopefully it'll get fixed in an update
the error is: Could not find "home/username/restart". please check the spelling and try again.
no idea what that's all about but who cares, its working again for the time being. as long as my dropbox is working I don't care, the box is headless anyways.

---

### Post by Shwefty on 2008-12-04
Heck, try just shortening "nautilus restart" to just "nautilus" in your Sessions.  It seemed to not like the "restart" part. :)

---

### Post by Apocrathia on 2008-12-04
tried that, it just opens a nautilus window then.

---

### Post by Ivo Moelans on 2008-12-04
You could try ***nautilus --quit***. This should restart nautilus afresh.

---

### Post by Apocrathia on 2008-12-04
changing my sessions item to "nautilus --restart" made everything work perfectly.

---

