---
title: "connection to the server was reset while the page was loading"
date: 2009-05-31
forum: General Help
---

### Post by dbworker on 2009-05-31
On loading certain pages Firefox under Ubuntu 9.04 returns:

"Connection Interrupted  

The connection to the server was reset while the page was loading.

The network link was interrupted while negotiating a connection. Please try again."

There are many mentions to this error but none of the suggestions I tried worked. (change dns, clear cookies and cache, change MTU settings)

This error only happens on certain pages. Slash dot RSS feed for example. Oddly the pages will load OK if the target page is loaded from the slashdot website directly but fails from the rss drop menu. The same page! On some sites the pics won't load.

All works OK when running XP on the same computer (different hard drive) with the same network settings.

The PC was working correctly for about 10 days before this trouble started.

Any suggestions?

Also, I would like to check that the browser cache files and cookies are really flushed. Where are the cache files stored?

How do you turn off IPV6? Instructions for previous Ubuntu versions don't seem to work on my machine. IPV6 is on on the machine by default.

Thanks

---

### Post by not applicable on 2010-07-03
I've had this issue on and off with a few linux distros and have also seen it happen on Windows.  I was able to resolve it on Mepis 8.5 by doing the following.

In firefox go to the edit menu > Preferences > Advanced, Click on the Encryption Tab and uncheck Use TLS 1.0. Ok it, and try the sites you were having issues with. Maybe even close and reopen the browser if this doesn't work right off.

Hope this helps.

---

### Post by dansk on 2012-11-04
Sorry to bump this old thread, but I just wanted to report that the solution in the previous post worked great for me.  Thanks!

---

