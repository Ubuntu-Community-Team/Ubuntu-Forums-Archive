---
title: "very strange disk space problem"
date: 2005-06-17
forum: Desktop Environments
---

### Post by bobgreen5s on 2005-06-17
I have a 5 gigabyte partition that is /home. Everything has been working fun until now where nautilus says that there is 785 megabytes free and 2.2 gigabytes in use. This does not make sense to me. Here is the screenshot.

[IMG]http://isoquad.com/huh.png[/IMG]

Any help would be appreciated.

---

### Post by jarrett.wold on 2005-06-17
"Tip: Find Large Files

Here’s a useful tip for both admins and users. Ever want to find what file or directory is taking up all of your space? On Linux, use the built in find utility like this:

find / -size +1000k -print -xdev

This does a search from /, finding all files greater than 100,000 kB and lists them. The -xdev merely tells find not to descend into directories on other filesystems. As always, RTFM."

- [http://aaltonen.us/archive/2003/04/26/tip-find-large-files/](http://aaltonen.us/archive/2003/04/26/tip-find-large-files/)

---

### Post by Xian on 2005-06-17
That command string will only tell you the space used and available on your mounted partitions. You have already narrowed it down further than that and we need to dig deeper. 

Issue the commands listed below.
Look for directories that seem oversized.

```
$ sudo du -sh /home/*
$ sudo sudo du -sh /home/your_user_name/*
```

---

