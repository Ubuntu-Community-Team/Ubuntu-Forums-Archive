---
title: "HDD churning periodically whilst online"
date: 2006-05-10
forum: Desktop Environments
---

### Post by snick on 2006-05-10
Hello Folks.
I am curious about churning of HDD when online.
What log can I access to determine cause of periodic HDD activity ?
Thanks,
-JS

---

### Post by hw-tph on 2006-05-11
Have a terminal window open running top.

My first guess is that the disk is making a lot of noise because updatedb is running, updating the slocate index. Disk usage usually peaks when this happens. It's nothing dangerous - slocate is a search tool which provides very quick response (as opposed to the find command) thanks to the search database.


Håkan

---

### Post by GrumpyBob on 2006-05-11
I'll try this - on my IBM Thinkpad R52 running Breezy, every so often HD activity escalates and the system functions so slowly that it effectively freezes.  Maybe this'll tell me what's going on...

Robert

---

