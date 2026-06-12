---
title: "Disappearing Folder - Any Way to Get It Back?"
date: 2005-09-18
forum: Desktop Environments
---

### Post by smittyinside on 2005-09-18
Well, I should have known better, but I forgot to rename the My Documents folder that I brought in from XP to a name without spaces. After a few days (and a restart), it appears to have disappeared without a trace. It's not showing up in the file tree, won't open in terminal, etc.  :?: I have backups, but they aren't bleeding edge, so I was hoping to be able to snag the few files that I changed in the past few days.

Any suggestions would be appreciated. Thanks!

---

### Post by Xian on 2005-09-19
If it is in the filesystem you can find it with the locate command.
First make sure you have updated your file database.

To find folders with spaces in the name you need to use quotes.

```
$ sudo updatedb
$ sudo locate "My Documents"
```

---

