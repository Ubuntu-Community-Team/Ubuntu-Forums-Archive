---
title: "Foomatic-rip"
date: 2006-06-08
forum: Desktop Environments
---

### Post by buser on 2006-06-08
Hey everyone,

Ever since upgrading to dapper, my Lexmark X73 printer has not worked correctly.  This is a multi function printer, and it worked perfect in breezy.  The error I get is :

"/usr/lib/cups/filter/foomatic-rip failed" when I go to [http://localhost:631](http://localhost:631) and click on jobs.  

The information from /var/log/cups/error_log is:

E [08/Jun/2006:21:04:18 -0600] [Job 6] /ioerror in --.outputpage--
E [08/Jun/2006:21:04:18 -0600] PID 6047 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!

I am using Kubuntu desktop and I tried a fresh install as well.
Any help would really be appreciated!

---

### Post by chrism7 on 2006-06-25
I have a similar problem.  I had this printer working on Breezy on a different PC, but now on Dapper it won't work.  Below is the output from my cups error log.  Any ideas how I fix this?

E [25/Jun/2006:21:23:22 +0800] [Job 12] No %%BoundingBox: comment in header!
E [25/Jun/2006:21:23:23 +0800] [Job 12] /ioerror in --.outputpage--
E [25/Jun/2006:21:23:23 +0800] PID 13718 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!

Thanks,
Chris

---

### Post by bobpaul on 2006-06-28
I get the same error on the properties page of the printer from the gnome-cups-manager and this error in my cups log:
```
E [28/Jun/2006:08:45:43 -0500] [Job 32] /ioerror in --.outputpage--
E [28/Jun/2006:08:45:43 -0500] PID 11286 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
```

I've never been able to get this printer working in Ubuntu (breezy or dapper) but it worked fine with the same /etc/cups/printers.conf on Gentoo.

[Edit]
I got it working! Look at the post by klytu in [this thread]("http://www.ubuntuforums.org/showthread.php?t=184838"). Basically, just sent the Version tag in /etc/pnm2ppa.conf. Maybe the same or similar can be done with your Lexmark only with the conf for the driver you use there.

Also, there is an Ubuntu note on the [Linuxprinting.org page]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-X73") for your printer.

---

### Post by Macchi on 2006-07-02
Similar problem with foomatic-rip!
I get the error code 1 from foomatic-rip in Dapper and started to wonder if is a bug instead of simply another configuration error of mine. Since other people are reporting similar symptoms there is a probability we are dealing with the same source for the problem.


Any suggestions on how to diagnose the foomatic-rip and cups in detail?
How to obtain detailed logs for debug?






Some complementary comments:
1) By the way, for the moment I cannot read Linuxprinting.org to access the foomatic FAQ.  

2) I can get the printer in question to work by calling the driver directly in a pipe from enscript and gs at the command line but I could not get it to work yet through cups+foomatic.

3) My printer is a portable Apple Color Stylewriter 2200 connected to the serial (!) port. A museum piece from 1996 that still works and is very useful together with a laptop. I am using the lpstyl driver patched for gcc 4 since the original source code had some strange type casting giving compile errors. 

4) My next step will be to test my printer driver together with cups+foomatic in Breezy. I Happen to have a reserve partition with Breezy on the same test machine, to be able to roll back just in case something would go wrong with Dapper. (I do thrust the Ubuntu comunity and Canonical, but it is good sometimes to have an extra safety line, I happen to know that from rock climbing.)

---

