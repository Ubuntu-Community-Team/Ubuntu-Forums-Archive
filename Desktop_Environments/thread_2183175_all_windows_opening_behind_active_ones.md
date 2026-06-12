---
title: "all windows opening behind active ones"
date: 2013-10-23
forum: Desktop Environments
---

### Post by clockworktri on 2013-10-23
I run Ubuntu 12.04.

All my windows have started opening behind whatever current one I have open. (This includes launching a new program, right-clicking to open in new window, etc.) I tried the solution listed at [this]("http://askubuntu.com/questions/162757/why-some-windows-in-ubuntu-12-04-opens-in-background") and [this]("http://ubuntuforums.org/showthread.php?t=1911406") post but it did not change anything. I don't know why it would start doing this, because I have not made any customizations recently. I do update my system whenever I can, so it may have started happening after an update. 

What should I do?

---

### Post by varunendra on 2013-10-25
Another place to check is in dconf settings. Open **dconf Editor** and browse to **org > gnome > desktop > wm > preferences**. Here, check the settings of **focus-mode**, **focus-new-windows** and **raise-on-click** options. Their default values are **click**, **smart** and **enabled** (ticked), and the optional values are mentioned in the "Description" section of the lower pane.

You may also try to enable the **disable-workarounds** option which is disabled by default. It is supposed to help in cases when a buggy application is causing this behaviour, but of course disables this kind of requests from the software.

---

