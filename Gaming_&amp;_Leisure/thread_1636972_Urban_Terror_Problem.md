---
title: "Urban Terror Problem"
date: 2010-12-03
forum: Gaming &amp; Leisure
---

### Post by Enigmapond on 2010-12-03
Hi!
I recently installed urban terror and really was liking it but today, it seems I can't get any servers from the master server. Any way to fix this?

Thank You!

---

### Post by RoflHaxBbq on 2010-12-04
Open console by pressing ~ whilst at the menu screen.

Type:

```
 /cl_master master.urbanterror.net
```Now see if it works. If it doesn't work, then type into console:

```
/cl_master master.quake3arena.com
```And now it should work.

-RoflHaxBbq

---

### Post by Soulcage on 2010-12-04
IMPORTANT! You must update this to fix the server list. If you don't do this you will not be able to get a server list from the master servers!

Please change your cl_master value by entering the following line into your console.
\cl_master "master.urbanterror.info"

Taken from: [http://www.urbanterror.info/news/central/cats/masters/]("http://www.urbanterror.info/news/central/cats/masters/")

---

### Post by Enigmapond on 2010-12-04
Right...I've tried doing what both you and the game site suggest and the game tells me that cl_master is not a valid command. I opened the config in my home directory and searched for this line...but there is no line for cl_master only sv_master so I changed THAT to what they suggest...saved and loaded the game and it still tries to pull from .net. Went back to the config and it had automatically changed back to .net even though I changed it to .info.

---

### Post by Enigmapond on 2010-12-04
For those still having this same problem, you can also follow this thread at the games' forum... [http://forums.urbanterror.info/topic/24243-no-servers/](http://forums.urbanterror.info/topic/24243-no-servers/)

---

### Post by Enigmapond on 2010-12-05
The old server is back online.... yay!

---

