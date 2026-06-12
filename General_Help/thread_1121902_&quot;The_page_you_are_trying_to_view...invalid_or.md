---
title: "&quot;The page you are trying to view...invalid or unsupported form of compression&quot; SOLVED"
date: 2009-04-10
forum: General Help
---

### Post by Filmorependrgn on 2009-04-10
Using Firefox 3.0.8, I get an error whenever I try to view some web pages as per the title of the post.

[example]("http://www.keithley.com/products/currentvoltage/?mn=2400")

Modifying the following about:config option to the following value fixes it:
```
network.http.accept-encoding  gzip,deflate;q=0.9,compress;q=0.7
```

---

