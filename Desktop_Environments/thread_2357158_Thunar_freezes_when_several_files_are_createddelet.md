---
title: "Thunar freezes when several files are created/deleted in quick succession"
date: 2017-03-30
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2017-03-30
I have a similar issue to [this thread]("https://ubuntuforums.org/showthread.php?t=2357100"), but I'm not sure it's quite the same, so starting a new thread.

I'm noticing the problem on both my bare-metal Xubuntu 16.04 and a VM of Xubuntu 16.04 (with the first machine as host).  I think the trigger for the problem happens under the following conditions -

1) Thunar needs to have been open, and in the background, for a bit.

2) In the folder which Thunar is displaying, several files getting created/deleted in quick succession.  For example, this occurs when running certain kinds of configure scripts.


When both those conditions are satisfied, not only is Thunar frozen, it doesn't even re-draw.  So, for example, after moving the frozen Thunar window, the area in the Thunar window where the Openbox position indicator was turns gray.


How to prevent these lockups?

---

### Post by &amp;KyT$0P# on 2017-04-04
Someone filed a bug report that looks exactly like this issue - [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1679488]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1679488") (notice comment #1)

---

