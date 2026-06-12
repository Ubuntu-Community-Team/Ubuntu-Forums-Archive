---
title: "folder not found??"
date: 2008-03-23
forum: Gaming &amp; Leisure
---

### Post by personalcrusade on 2008-03-23
An error occurred while trying to apply an update to EVE Online for Linux. The directory /home/vankirk/.cedega/EVE Online does not seem to exist. If you renamed the folder, please unrename it. If that doesn't work, you might need to obtain a fresh install of the game.

thats what I get when I try to install eve online although I checked and it is where it's suppose to be anyone else have this problem??

---

### Post by kbless7 on 2008-03-23
With files with spaces in the name, you have two options for pointing to it.

Either by doing quotes
```
"/home/vankirk/.cedega/EVE Online"
```

Or by using forward slashes
```
/home/vankirk/.cedega/EVE\ Online
```

In your case you might have to do a symbolic link to that file.

---

