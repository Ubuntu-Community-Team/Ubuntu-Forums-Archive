---
title: "Downloading recursively using gwget"
date: 2009-02-21
forum: General Help
---

### Post by 7raTEYdCql on 2009-02-21
I am trying to download a site recursively to a depth of 1 using gwget. Every time i change the preferences and start my download the preferences get reset and all i get is the title page, with none of the links downloaded.

Can someone guide me with the use of gwget to download entire webpages.

---

### Post by yeleek on 2009-02-21
Afraid can't help with gwget but have you tried straight vanilla wget?

Very easy

wget -r "http://site.com"

or better

wget -r -l "http://site.com"

with -l number being 
-l,  --level=NUMBER       maximum recursion depth (inf or 0 for infinite).

---

### Post by alphaamanitin on 2011-03-17
Where does it save these files to?  I am trying to wget a book that is availabe in html format from a linux website for offline viewing, but I couldn't get gwget to work recursively and I cannot find where wget is saving my looks busy file (command line is flying like mad!)

AlphaA

---

### Post by linuxonbute on 2011-03-17
> **alphaamanitin said:**
> Where does it save these files to?  I am trying to wget a book that is availabe in html format from a linux website for offline viewing, but I couldn't get gwget to work recursively and I cannot find where wget is saving my looks busy file (command line is flying like mad!)

AlphaA
The directory you are running wget from.
Never used gwget but installed it and when it starts up it shows you where it is going to download to but gives you the option to change this.
However all it does is download index.html even if you add the recursive option!!!!!!
So i guess it's broken.

---

