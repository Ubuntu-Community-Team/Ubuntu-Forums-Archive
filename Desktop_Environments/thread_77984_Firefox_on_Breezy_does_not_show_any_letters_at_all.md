---
title: "Firefox on Breezy does not show any letters at all"
date: 2005-10-17
forum: Desktop Environments
---

### Post by calamari on 2005-10-17
I have just upgraded to Ubuntu Breezy, and now this is what Firefox looks like:

[IMG]http://kidsquid.com/ubuntu_firefox_bug.png[/IMG]

or a link in case the above doesn't show up:

[http://kidsquid.com/ubuntu_firefox_bug.png]("http://kidsquid.com/ubuntu_firefox_bug.png")

It is impossible to use.. as you can see, the menus, webpages, etc have no letters showing.  

Here is the result of running strace with firefox:

[http://kidsquid.com/ubuntu_firefox_bug.strace.txt]("http://kidsquid.com/ubuntu_firefox_bug.strace.txt")

Here is what firefox prints in the console when run:

[http://kidsquid.com/ubuntu_firefox_bug.console.txt]("http://kidsquid.com/ubuntu_firefox_bug.console.txt")

Here is the output of firefox --version:

```
Mozilla Firefox 1.0.7, Copyright (c) 1998 - 2005 mozilla.org
```

I have renamed .mozilla to .mozilla.old and ran firefox that way, same problem.
Please help me get firefox working again.

Thanks.

---

### Post by calamari on 2005-10-17
Fixed!! 

I was poking around in Synaptic and noticed that yelp had not been upgraded.  I decided to check why.  It needed firefox, and needed to uninstall ubuntu-firefox, and ubuntu-firefox-gnome-support (I don't remember the exact name of this 2nd package, but that's close).  So if you have this problem, here should be the fix:

* Mark firefox for install.  I think this will mark ubuntu-firefox for uninstall.  Do the remove/install and things should be fixed.

---

