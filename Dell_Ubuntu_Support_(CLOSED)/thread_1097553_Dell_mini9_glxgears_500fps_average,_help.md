---
title: "Dell mini9 glxgears 500fps average, help"
date: 2009-03-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by starcannon on 2009-03-16
Hello, 
I'm trying to get my mini9 to at least keep up or surpass my Asus Eee 701.
Currently my Mini9 gets around 500 fps on glx gears, and my Asus Eee is averaging 650 fps on glxgears.

Does anyone know the how and why of this?

---

### Post by sirebral on 2009-03-16
Run this on both systems

```

lspci -v -s 00:02.0

```

It will tell you the amount of Video RAM. That might be an indication.

---

### Post by ssam on 2009-03-18
glxgears is not a benchmark.
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)
[http://qa-rockstar.livejournal.com/7869.html](http://qa-rockstar.livejournal.com/7869.html)

---

