---
title: "Home Site"
date: 2006-01-06
forum: General Help
---

### Post by doug.barrett on 2006-01-06
I am sure I am just missing some miniscule detail here, but I have a few questions.

I just installed Apache2, php4 and all of the mysql things on my PC, and it all works fine (I tested the PHP site) and from the PC I can go to 'http://localhost/testphp.php' and it will show me the site.

I can't however connect to that page from my laptop.

It too is running Ubuntu, but I doubt that really matters.

Is this a quick fix to get the site shared on the server?

And also, I was wondering how you change 'localhost' to be something like 'familysite'?  I thought I could change it in the httpd file, but I can't seem to find it.

Thanks!

---

### Post by doug.barrett on 2006-01-06
bump

please, any help would be much appreciated, thanks :)

---

### Post by FizDev on 2006-01-06
Just to be sure... what did you enter to see your website on the pc from your laptop?

[http://localhost/](http://localhost/)
or
[http://ipofthepc/](http://ipofthepc/)

---

### Post by doug.barrett on 2006-01-06
I used the name of the PC.

I'm going to restart the process and try it again.

---

### Post by FizDev on 2006-01-06
In that case, did you try to ping the other computer?
If it responds and you cannot access your server from your other computer then it is probably your server configuration.
Personnally, I followed this :
[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28Apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28Apache%29)
and didn't got any trouble. Maybe it will help you :)

If it doesn't respond then... it might just be your network, and not the server configuration itself.

---

