---
title: "Missing rgb.txt"
date: 2008-10-31
forum: Desktop Environments
---

### Post by svamppi on 2008-10-31
Hi,
I installed the xubuntu 8.10 beta (or was it RC, not 100% sure) and had trouble getting 256 colors working in my terminal so I installed ncurses-term, however it still didn't work. So I noticed that bash was whining about a missing or incorrect rgb.txt. So I located rgb.txt and found out it was empty. So I fixed it manually by finding a replacement for it online. However I recently upgraded some packages and then rgb.txt was empty again. Any ideas what's wrong? I noticed other people had similar problems back in 2005 and 2006. But the packages recommended to install in those cases have been replaced by others now and installing them doesn't do anything.

---

### Post by bromalex on 2008-11-07
Hi!
Nobody answered so far, but I found exactly the same issue.
/usr/share/X11/rgb.txt is a broken link to /etc/X11/rgb.txt which doesn't exist.
Can anybody help?
Thanks

PS: Let me also say hello to everybody, as this is my first message to Ubuntu Forums as a newcomer to the wonderful world of Linux with my 8.10 Intrepid instalation.

---

### Post by svamppi on 2008-11-23
The reason I was asking about this was that I wanted to use the CSApprox plugin for vim which needs it. Well, the author of the plugin told me that newer versions of X have stopped providing this as a standard file and instead compiled the information into some binary somewhere instead. So the newest version of the CSApprox plugin now comes with its own rgb.txt. I still don't see why there should be a dangling symlink to that file though. If you need the file I suggest downloading it manually (I just googled for it) and putting it somewhere and redirecting the link.

---

### Post by bromalex on 2008-11-23
Thank you svamppi.
I was trying to find the name of the colors to use in conky.
Meanwhile i have been using this page
[http://sedition.com/perl/rgb.html](http://sedition.com/perl/rgb.html)
But now I have googled for the file :-)

---

