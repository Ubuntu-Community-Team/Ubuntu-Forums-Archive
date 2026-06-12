---
title: "Evolution web links not finding Shiretoko"
date: 2009-09-23
forum: Desktop Environments
---

### Post by cpeachey on 2009-09-23
I have upgraded Firefox to Shiretoko and removed the old firefox.
Web links in Evolution e-mails are still looking for Firefox. How do I make it look for Shiretoke please?
Chris

---

### Post by laceration on 2009-09-23
In your /usr/bin folder you have firefox-3.5, which is shiretoko.  If you make a symbolic link to this and name it firefox it should remedy your problem.  You have to do this as root, so open nautilus like this:
```

sudo nautilus /usr/bin

```
If there is a firefox already there it is a symbolic link to your old firefox, delete it.
Then right click firefox-3.5, select make link and rename the link firefox.

---

