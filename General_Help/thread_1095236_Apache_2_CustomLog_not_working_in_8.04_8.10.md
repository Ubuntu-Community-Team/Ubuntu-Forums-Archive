---
title: "Apache 2 CustomLog not working in 8.04 8.10"
date: 2009-03-13
forum: General Help
---

### Post by dananarama on 2009-03-13
I am experiencing a problem I have found posted here:

[http://www.tek-tips.com/viewthread.cfm?qid=1529353&page=1](http://www.tek-tips.com/viewthread.cfm?qid=1529353&page=1)
[http://stackoverflow.com/questions/525057/customlog-not-working-in-apache2-on-ubuntu-8-10](http://stackoverflow.com/questions/525057/customlog-not-working-in-apache2-on-ubuntu-8-10)


I am using Ubuntu 8.04 and Apache 2.2.8.  

The CustomLog and TransferLog directives under apache appear to do nothing.  The empty files are created, but nothing appears in them.  This occurs even if I use a non-conditional, simple log format of "hello" or "%u". 

In my case, the module mod_log_config is compiled into Apache, so I cannot attempt to update the mod_log_config.so file.  Can someone give me advice as to what would happen if I attempted to recompile the apache binary with the same modules it currently uses?  Would this have a low impact on the system?

Like the user above, I am stumped at this point.  I would like to get custom logging working, but may have to wait for the next Ubuntu apache release.

Thanks,


Dan

---

### Post by dananarama on 2009-03-13
I wanted to add that this issue cropped up because I was attempting to log SubVersion access using apache CustomLog as detailed in many places such as here:

( SubVersion book -- apache logging )

[http://svnbook.red-bean.com/en/1.5/svn.serverconfig.httpd.html#svn.serverconfig.httpd.extra.logging](http://svnbook.red-bean.com/en/1.5/svn.serverconfig.httpd.html#svn.serverconfig.httpd.extra.logging)


Thanks for any help,


Dan

---

### Post by kyle2222 on 2009-03-24
I've encountered the exact same problem with CustomLog (0 byte file).

Version information:
Server version: Apache/2.2.8 (Ubuntu)
Server built:   Mar 10 2009 18:09:05

---

### Post by dananarama on 2009-03-24
It's good to see a reply here.

Anyone know when a new version of Apache will be out for Ubuntu Hardy (8.04)?

---

### Post by dananarama on 2009-03-24
Reported the issue here:

[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/347992](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/347992)

---

### Post by Niffy on 2009-04-06
Any luck?
I've found that on my Debian EEE Lenny using Apache 2.2.9 the same thing happens.  My Ubuntu 8.04 Apache 2.2.8 does the same as well.
This is very anoying, Apache can save me a lot of time in my project.

---

### Post by dananarama on 2009-10-02
> **Niffy said:**
> Any luck?
I've found that on my Debian EEE Lenny using Apache 2.2.9 the same thing happens.  My Ubuntu 8.04 Apache 2.2.8 does the same as well.
This is very anoying, Apache can save me a lot of time in my project.


This issue remains.  I updated the status here:

[https://bugs.launchpad.net/ubuntu/+s...e2/+bug/347992](https://bugs.launchpad.net/ubuntu/+s...e2/+bug/347992)

---

