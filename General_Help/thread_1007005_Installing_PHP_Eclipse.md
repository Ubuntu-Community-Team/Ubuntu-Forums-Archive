---
title: "Installing PHP Eclipse"
date: 2008-12-09
forum: General Help
---

### Post by OneSeventeen on 2008-12-09
I'm a sucker that paid for Zend Studio for Eclipse, but I'd like to see how far I can go on free software, especially if it is Open Source.

The irony is I could not get PHP Eclipse running under the open source java runtime (gcj), so here's what I did to get PHP Eclipse working for me:
[list=1]
[*]uninstall any traces of gcj
[*]download and extracted Eclipse from [http://www.eclipse.org](http://www.eclipse.org)
[*]Add the proper Update Site for your version of Eclipse and download/install PHP eclipse (instructions on the [PHP Eclipse Installation Page](http://www.phpeclipse.de/wiki/Installation))
[*]Restart Eclipse and choose the PHP Perspective from Window>Open Perspective>Other
[/list]

That's what I did, and it seemed to work great.  I had to totally remove Eclipse and any forms of gcj, then install the latest version of Eclipse.

I [blogged about installing PHP Eclipse in Ubuntu 8.10](http://woventhorns.blogspot.com/2008/12/how-i-got-php-eclipse-running-in-ubuntu.html), but I'm not a good blogger, so I went ahead and copied a simplified version here.

Before doing this, I kept getting the errors about > An error has occurred. See error log for more details.

Hope this helps someone else!

---

### Post by aetern on 2009-02-19
Thanks for helpful information. :)

---

