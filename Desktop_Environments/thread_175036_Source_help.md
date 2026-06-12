---
title: "Source help"
date: 2006-05-12
forum: Desktop Environments
---

### Post by deathbyswiftwind on 2006-05-12
My friend since he only has dial up cannot download all the files he needs (in a matter of time). I am using instructions to make dvd copies of the cargol mirror. The only thing Im not sure of is how does he add the dvds as sources? In dapper you click add cdrom or whatever and it sets it up for you. Can someone please help

---

### Post by tonyr on 2006-05-12
Look at **apt-cdrom**.  It handles dvd, too. The usual command seems to be
```

sudo apt-cdrom -d=<device-mount-point> add

```

I've never used it, so check it out thoroughly before you advise someone else.

EDIT: Here's a thread similar to yours:
[URL="http://www.ubuntuforums.org/showthread.php?t=164712"]
http://www.ubuntuforums.org/showthread.php?t=164712[/URL]

---

