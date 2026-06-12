---
title: "Tracker does not index .php files"
date: 2010-11-12
forum: Desktop Environments
---

### Post by pled on 2010-11-12
Hi,
I am using Ubuntu 10.10 and Tracker 0.8.17, and realized that Tracker does not index .php files. 
In the tracker-extract log, I can read :

> Could not find any extractors to handle metadata type (mime: application/x-php)

Then I found that in /usr/lib/tracker-0.8/extract-modules directory is a list of extractors modules, like : libextract-html.so, libextract-text.so, etc...
So I guess that for each mime type, you need a specific extractor.

I was expecting that .php files, because they contain text, would be indexed as well. 

What can be done to make tracker indexes such text files ?
Thank you.

---

