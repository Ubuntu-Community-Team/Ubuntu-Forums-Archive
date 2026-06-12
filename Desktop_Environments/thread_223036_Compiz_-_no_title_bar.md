---
title: "Compiz - no title bar"
date: 2006-07-25
forum: Desktop Environments
---

### Post by spin2cool on 2006-07-25
I followed this guide to setting up compiz on Ubuntu:
[http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/](http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/)

It seemed to work fine for the most part, but I am unable to see any title bars.  (I can run  "metacity --replace", but I'd like to use the compiz titlebars)

When I run gcompizthemer, I have themes installed, and under "general" I do have "use pixmap buttons" checked and a title-bar object layout selected.  

What am I missing here?!

---

### Post by spin2cool on 2006-07-25
Never mind.  By running the command:

compiz --replace gconf &

I was able to get it working.

---

