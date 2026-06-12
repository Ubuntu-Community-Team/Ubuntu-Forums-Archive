---
title: "How to change the dansguardian.pl access denied page"
date: 2006-08-29
forum: Desktop Environments
---

### Post by rjeeves33 on 2006-08-29
Hi guys

I've just installed Ubuntu, dansguardian, apache & tinyproxy.  It's all working swell but I want to modify the access denied page.  Anyone know how to do this?  

My dansguardian.conf sets the accessdenied = [http://192.168.1.1/cgi-bin/dansguardian.pl](http://192.168.1.1/cgi-bin/dansguardian.pl)

So I modify this file by changing the title  but the denied page served by dans is not changed.  It must be serving the page I'm seeing from somewhere else :)  But where?  The path to the danguardian.pl I modified is /usr/www/cgi-bin/dansguardian.pl.

Any ideas? It's doing my brain in ](*,) 

Thanks

---

### Post by tonhou on 2006-08-29
I think you are looking for:

/etc/dansguardian/languages/ukengish/template.html

(in the case of the English block page)

There are several different style of block pages found here:

[http://dansguardian.org/?page=extras](http://dansguardian.org/?page=extras)

--Tony

---

### Post by rjeeves33 on 2006-08-30
Awesome. That worked a treat.  Thanks for your help

---

