---
title: "gkrellm version 2.2.10"
date: 2007-02-04
forum: Desktop Environments
---

### Post by computx on 2007-02-04
I don't find the latest gkrellm anywhere in the repos or online. 
2.2.10 added support for SSL in POP mail which I really needed. So I rolled my own using checkinstall.  This is for on an edgy eft x86 system. No guarantees this will work on your system but thought I would share.
 [http://computx.us/blog/index.php?/archives/9-gkrellm-2.2.10-with-SSL-goodness!.html](http://computx.us/blog/index.php?/archives/9-gkrellm-2.2.10-with-SSL-goodness!.html)

---

### Post by Arup on 2007-02-05
Thanks, works fine on my dual P-II machine with Edgy generic SMP kernel, only thing is it doesn't get listed uder applications but thats nothing major.

---

### Post by computx on 2007-02-05
Since I am green at making .debs and had trouble doing it the "official way" I used checkinstall. That is probably why the menu item was not created. Glad it works for you.

---

### Post by yabbadabbadont on 2007-02-05
> **computx said:**
> I don't find the latest gkrellm anywhere in the repos or online. 
2.2.10 added support for SSL in POP mail which I really needed. So I rolled my own using checkinstall.  This is for on an edgy eft x86 system. No guarantees this will work on your system but thought I would share.
 [http://computx.us/blog/index.php?/archives/9-gkrellm-2.2.10-with-SSL-goodness!.html](http://computx.us/blog/index.php?/archives/9-gkrellm-2.2.10-with-SSL-goodness!.html)

I don't understand, my 2.2.7 version has a "Use SSL?" option on the pop configuration screen...

---

### Post by computx on 2007-02-06
Can't say what 2.2.7 had but it was definitely missing from my 2.2.9 install. If you go to the gkrellm home page it specifically mentions in the changelog that 2.2.10 added ssl support for pop3.

Maybe you are using a mail checker plugin rather than the builtin one?

---

### Post by yabbadabbadont on 2007-02-07
> **computx said:**
> Can't say what 2.2.7 had but it was definitely missing from my 2.2.9 install. If you go to the gkrellm home page it specifically mentions in the changelog that 2.2.10 added ssl support for pop3.

Maybe you are using a mail checker plugin rather than the builtin one?

Nope, just the builtin one.  I haven't actually used the SSL option, I just see that it is there for remote pop mailboxen.

---

