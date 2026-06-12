---
title: "Firefox downloading .phtml files"
date: 2006-09-25
forum: Desktop Environments
---

### Post by lozenge on 2006-09-25
Firefox won't work with PHPMyAdmin, or anything with file extensions other than html and php.

Any ideas why, and what I can do to fix it?

---

### Post by andypaxo on 2006-09-25
When web browsers try to download web pages instead of displaying them, it is usually due to the server not sending the right data - rather than the web browser itself.

If this is your own PHPMyAdmin installation - you might want to check your server setup (Apache?). Make sure phtml is being treated as PHP.

If this is the case, you might want to look at:
[http://www.faqts.com/knowledge_base/view.phtml/aid/9546/fid/51](http://www.faqts.com/knowledge_base/view.phtml/aid/9546/fid/51)

Hope this helps

---

### Post by bishop7 on 2006-09-30
I am also having this problem.  This did not fix it.  Apache will run .php scripts just fine, and I added those lines but it didn't appear to make any difference.  

When attempting to load the .phtml file, it tries to download the file over and over again.  It appears to be opening the file from the /tmp directory and even identifies the file as a 'PHP script.'  The .phtml file has a random name, as well.

I ran through the steps in this document as well:

[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29)

---

### Post by Dragon_52 on 2006-10-01
I had this problem too - straight after I installed Apache/PHP. It turned out that flushing Firefox's cache (clearing History, etc) was the little missing step.

Hope it works for you.

---

