---
title: "Rhythmbox cyrillic"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Dgurion on 2005-10-15
Anyone know how to get Rhythmbox to display cyrillic characters?

---

### Post by doclivingston on 2005-10-15
Do you mean Rhythmbox itself, or the contents of tags such as titles and artists?

If it's that latter, the problem is usually that the tags edited with a tag-editor that is broken and doesn't write them properly, and unforunately almost every Windows tag editor is broken like this. The problem is that they store the tags in the current locale while setting the header to ISO-8859-1, which is wrong. Some other programs have hacks to get around this, but Rhythmbox hasn't included those in a long time, because they cause problems for some people whose taggers work correctly.

One of the bugs filed about this against Rhythmbox has a link to a program that might fix the tags (although I haven't tested it myself): [http://www.cs.berkeley.edu/~zf/id3iconv/](http://www.cs.berkeley.edu/~zf/id3iconv/)

---

