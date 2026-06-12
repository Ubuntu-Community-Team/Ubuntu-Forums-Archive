---
title: "From localhost to example.com In Apache ?"
date: 2010-02-25
forum: Desktop Environments
---

### Post by saidbakr on 2010-02-25
Hello
In some web applications related tutorials I noticed that the introducer use something like [www.example.com](www.example.com) to access the local apache server on his computer.

I wonder, how could he able to do that?

In addition I need to know, does it possible to access my local Apache web server on my Ubuntu computer from multiple addresses beside localhost, for examle:
myproject.com
theblog.net
etc

and each domain has its own document root.

---

### Post by Kakers on 2010-02-25
I imagine he is probably using Virtual hosts in apache [http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

example:
<VirtualHost 127.0.0.1>
       DocumentRoot /www/example
       ServerName [www.example.com](www.example.com)
       </VirtualHost>

<VirtualHost 127.0.0.1>
       DocumentRoot /www/testing
       ServerName [www.testing.com](www.testing.com)
       </VirtualHost>

Don't know too much about this myself, but have fun!

---

### Post by Kakers on 2010-02-25
Here is a good example:
[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by saidbakr on 2010-02-25
> **Kakers said:**
> Here is a good example:
[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

In the tutorial you regarded something about creating symbolic links in some folders. Does it correct to use right mouse click then choose make link then copy the link file to the targeted directory?

---

