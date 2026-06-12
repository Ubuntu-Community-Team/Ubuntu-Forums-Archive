---
title: "Alias - virtual directory"
date: 2009-06-03
forum: General Help
---

### Post by Intuit on 2009-06-03
Hi,

I am trying to create a virtual directory and I have read and followed this thread to the T,
[http://ubuntuforums.org/showthread.php?t=280751](http://ubuntuforums.org/showthread.php?t=280751). But, without any success.

I have put the code both in /etc/apache2/sites-available/default and /etc/apache2/conf.d/alias as suggested. But, I am not getting a 403 error. Rather I get a 404 error.

**Not Found**

 The requested URL /files was not found on this server.


Can someone help me please!


Thank you,
Thomas

---

### Post by blueridgedog on 2009-06-03
You may get more specific help on a forum specializing in apache setup.

When I setup apache (a long time ago) I typically would tail the server error log when debugging a setup.  Generally this gave some useful information.  I would restart the server, check the error logs for a clean start, then attempt hit the site I was debugging and trace out errors in the logs.

---

