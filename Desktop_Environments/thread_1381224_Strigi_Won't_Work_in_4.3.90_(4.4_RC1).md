---
title: "Strigi Won't Work in 4.3.90 (4.4 RC1)"
date: 2010-01-14
forum: Desktop Environments
---

### Post by markthefart on 2010-01-14
When I Enable Strigi Desktop Search, it immediately crashes and I get about 20 popups that say: Nepomuk Indexing Agents have been disabled. and Needs Virtuoso RDF Server to store it's data. I'm running Kubuntu 9.10 and I've upgraded to KDE 4.3.90. (4.4 RC1) Anybody know anything about it or how to enable desktop search??
Here's a screen.. Thanks Mark

[[IMG]http://img25.imageshack.us/img25/471/snapshot3l.png[/IMG]](http://img25.imageshack.us/i/snapshot3l.png/)

---

### Post by Zorael on 2010-01-14
Going by the error message, try installing the **virtuoso-server** package (and perhaps the **virtuoso-drivers** one, too).

[http://trueg.wordpress.com/tag/virtuoso/](http://trueg.wordpress.com/tag/virtuoso/)

---

### Post by markthefart on 2010-01-14
Perfect! Thanks!!

Kolia wrote:
I got mine on this PPA: [https://launchpad.net/~jr/+archive/ppa](https://launchpad.net/~jr/+archive/ppa) (this is Jonathan Riddell PPA, quite trustable  )

Install the virtuoso-opensource package from there, that should do the trick.

---

