---
title: "&quot;Places&quot; menu does not open files"
date: 2011-01-23
forum: Desktop Environments
---

### Post by otblee on 2011-01-23
After installing auto upgrade to allow temporary access to root directory, the Places menu does not open file folders.   If I switch users it works fine.

---

### Post by Krytarik on 2011-01-24
What else happens, maybe it launches a program?

Open the file "~/.local/share/applications/mimeapps.list" and lookup the option for "inode/directory", the line should look like this:
```
inode/directory=nautilus-folder-handler.desktop;
```

---

### Post by otblee on 2011-01-24
Thanks for the response, I found an earlier post that had me create a new file, go to "open with other applications" then select "open folder". Every thing is fine now.

---

### Post by Krytarik on 2011-01-24
> **otblee said:**
> Thanks for the response, I found an earlier post that had me create a new file, go to "open with other applications" then select "open folder". Every thing is fine now.
Yeah, that's another way to achive virtually the same. In fact, it just puts "nautilus-folder-handler.desktop" in front of the mentioned line, before the faulty one.

---

