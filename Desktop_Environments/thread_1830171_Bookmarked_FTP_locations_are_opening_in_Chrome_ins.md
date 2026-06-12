---
title: "Bookmarked FTP locations are opening in Chrome instead of Nautilus"
date: 2011-08-21
forum: Desktop Environments
---

### Post by rotten777 on 2011-08-21
So I've got a connection to a non-anonymous FTP server and bookmarked it like all my other connections. For some reason, if I click Places->HSS (the name of the bookmark), it opens the url in chrome as:

Index of /home/local/.gvfs/ftp as username on ip

I've run around in the gconf-editor and cannot find anything pulling the chrome executable in regards to this.

Is there a fix? Firefox is the default browser and I've set that everywhere I can find.

Thanks in advance.:)

---

### Post by rotten777 on 2011-08-21
```
To fix it, follow these steps:
1) Open gconf-editor from a terminal
2) Navigate to /desktop/gnome/url-handlers/ftp
3) change the command value to nautilus %s
```

Whoops.. Not solved. Still same issue.

---

