---
title: "Having trouble with xmlstarlet"
date: 2009-02-27
forum: General Help
---

### Post by shaggy999 on 2009-02-27
I am trying to use xmlstarlet to search through the ubuntu package rss feed and print out a list of packages but I can't seem to get it to work.

Here's the rss feed: [http://packages.ubuntu.com/intrepid-updates/newpkg?format=rss](http://packages.ubuntu.com/intrepid-updates/newpkg?format=rss)

Here's my terminal command:

```
curl -s http://packages.ubuntu.com/intrepid-updates/newpkg?format=rss | xmlstarlet sel -t -m "//title" -v "." -n
```

This does not seem to work. In fact, I can't seem to get any example code to work when I try to apply it to this rss feed. The only thing I can do is print out the entire xml file by changing "//title" to "/".

Does anybody have any ideas on how to get this to work? I'm using the standard xmlstarlet package in the repository.

---

### Post by shaggy999 on 2009-02-28
I figured out my problem. XPath requires that namespaces be used if they are defined in the XML file, so xmlstarlet requires them as well. The solution is here: [http://xmlstar.sourceforge.net/doc/UG/xmlstarlet-ug.html#d0e673](http://xmlstar.sourceforge.net/doc/UG/xmlstarlet-ug.html#d0e673)

For reference, here's my code that works:

```
curl -s 'http://packages.ubuntu.com/intrepid-updates/newpkg?format=rss' | xmlstarlet sel -N x="http://purl.org/rss/1.0/" -t -m "//x:item/x:title" -v '.' -n
```

---

