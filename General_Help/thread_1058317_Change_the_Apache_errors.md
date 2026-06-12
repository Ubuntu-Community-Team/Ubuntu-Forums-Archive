---
title: "Change the Apache errors?"
date: 2009-02-02
forum: General Help
---

### Post by linuxisevolution on 2009-02-02
I would like to change the page that shows when you try to go to a link that does not exist. Were should this page reside? Can I make Apache redirect to a certain page if it doesn't load?

---

### Post by sedawk on 2009-02-02
I think you have to add a line like
```

ErrorDocument 404 myown404.html

```
to your httpd.conf, but check the apache doc
for more documentation of "ErrorDocument" parameter.

---

### Post by linuxisevolution on 2009-02-02
I would like it to redirect to this page I made :)

[http://24.3.84.251/apache2-default/mac/mac/Default.html](http://24.3.84.251/apache2-default/mac/mac/Default.html)

---

