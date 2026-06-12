---
title: "Trouble Install Cricket"
date: 2006-01-17
forum: Desktop Environments
---

### Post by poison on 2006-01-17
Hi

I used apt-get to install cricket and all went 100%, it install Cricket version 1.0.5 with no hassles. 

I am trying to configure this now and when I try and follow the documentation on [http://cricket.sourceforge.net/support/doc/beginner.html](http://cricket.sourceforge.net/support/doc/beginner.html) I am getting a bit lost.

Does any one know where the routers directory and where the Targets file needs to reside as it appears the installer installed into cricket/usr/share/cricket and config files into /etc/cricket/.

I followed the documentation in the link above but when I get to running 
./collector /routers  I get all these errors

/usr/share/cricket# ./collector /routers -logLevel debug
[17-Jan-2006 17:32:22 ] Log level changed from warn to debug.
[17-Jan-2006 17:32:22 ] Starting collector: Cricket version 1.0.5 (2004-03-28)
[17-Jan-2006 17:32:22*] Unknown subtree /routers.
[17-Jan-2006 17:32:22*] Unknown subtree /routers.
[17-Jan-2006 17:32:22 ] Processed 0 targets in 0 seconds

Has anyone successfully got Cricket working on ubuntu and if so can you help

Thanks

---

### Post by poison on 2006-01-17
Okay I found that the Targets file needs to reside in /etc/cricket/config/

The thing is now when I run the ./collector command I get the follwoing errors :-

 /usr/share/cricket# ./collector
[17-Jan-2006 18:11:51 ] Log level changed from warn to info.
[17-Jan-2006 18:11:51 ] Starting collector: Cricket version 1.0.5 (2004-03-28)
[17-Jan-2006 18:11:51*] No ds tag found for target type cisco-2500-router.
[17-Jan-2006 18:11:51*] No ds tag found for target type cisco-2500-router.
[17-Jan-2006 18:11:51 ] Processed 2 targets in 0 seconds

Any ideas?

---

### Post by deontaljard on 2006-01-17
Looks like you might need a defaults file for that router.  I had a brief look at this
[http://sourceforge.net/mailarchive/forum.php?forum_id=6693&max_rows=25&style=nested&viewmonth=200005](http://sourceforge.net/mailarchive/forum.php?forum_id=6693&max_rows=25&style=nested&viewmonth=200005)

-Deon

---

### Post by deontaljard on 2006-01-17
Do you have a quick and easy install "How to" for the Perl modules - let me see if I can get my install to the same point as yours.

---

