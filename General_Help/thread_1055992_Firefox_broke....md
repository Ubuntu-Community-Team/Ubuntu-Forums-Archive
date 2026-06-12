---
title: "Firefox broke..."
date: 2009-01-31
forum: General Help
---

### Post by tom66 on 2009-01-31
My Firefox is broken.

 - I can't view downloads - segmentation fault.
 - I can't view addons and modify them - segmentation fault.
 - Back/forward buttons constantly disabled.
 - Search box is unavailable - typing into it works but searching is not possible. However typing nothing brings me to Google Firefox homepage. 
 - Firefox starts up and asks me if I want to restore session, even if no crash happened before.
 - Firefox always starts up with default settings: a bookmarks toolbar - empty, and only 1000-ish pixels wide.

I have disabled all addons. 

How can I fix this? I am typing this in Firefox at the moment and would prefer to keep using it. Also I am writing this in Ubuntu 8.10. The problems seemed to appear after updating Ubuntu but I can't be sure.

---

### Post by yoman82 on 2009-01-31
I have the same issue, it won't even accept my backed-up file.

---

### Post by hyperdude111 on 2009-01-31
your best option is to completeley remove firefox.

So go to synaptic and completley remove firefox.

Then go to your home folder and enable hidden files and folders. Delete the .mozilla folder.

Then go to usr/share/ and delete the .mozilla and .firefox folders. 

Once this is done go back to synaptic and re-install firefox.

_________________

This will however remove all of your firefox settings, addons and bookmarks but it is the best i can do.

---

### Post by yoman82 on 2009-01-31
Why? That would take HOURS to fix. Is there an easier way? I'd prefer not to remove all of my configuration.

---

### Post by procastino on 2009-02-09
Exactly the same happens to me, anyone found a solution without deleting firefox settings?

---

### Post by skynexus on 2009-02-11
Upgrade FAIL!

The latest update has broken firefox. Can't see add-ons, several settings tab etc.

Help FAIL!

No, I will not wipe the bookmarks I have accumulated for 12+ years.

If I was not so occupied I would file a bug report ASAP but I'm busy (and this is not helping). Very annoying to say the least.

On a related note, everytime my firefox starts it has been in this weird quasi-fullscreen mode (compiz basic settings on). Was hoping this would fix that. Damn.

---

### Post by skynexus on 2009-02-11
Fixed. I think it was my (very stupid) mistake, had another firefox window in another desktop running that I never noticed during and after the update.

In other words, make sure firefox exits completetly (no running process anywhere), the start it again.

---

### Post by geirha on 2009-02-11
Try reinstalling firefox. ```
sudo aptitude reinstall firefox-3.0
```

---

