---
title: "What's the deal with Beagle?"
date: 2006-11-11
forum: Desktop Environments
---

### Post by Peepsalot on 2006-11-11
I don't understand what this beagle program is supposed to do.  It only returns partial results for the files I'm looking for.

If I run this command in terminal
```
find / -iname *partial_file_name* 2> /dev/null
```
I get more results than beagle gives.

I setup Beagle to index from the root directory "/", but it doesn't seem to be doing it right.

Is there some nice GUI program that can perform the equivalent of the command I posted?

---

### Post by ciscosurfer on 2006-11-11
Beagle only sometimes works for me.  I know what you mean.

---

### Post by Peepsalot on 2006-11-11
Well at least i'm not the only one.  

I just wrote up a script to aide me in searching for files if you are interested.
[http://www.ubuntuforums.org/showpost.php?p=1743226&postcount=36](http://www.ubuntuforums.org/showpost.php?p=1743226&postcount=36)

---

### Post by .t. on 2006-11-11
It's designed for indexing home directories. It looks in the files, not just at the names. It needs to form an index of the files first, before you can find them. For the whole system, this'll take a while. locate and find are proabably better commands to use outside the home directory, in my opinion :)

---

### Post by pveith on 2006-11-11
As a test on how beagle works, just open a beagle query on "whateveryouwant" and leave it on screen, while using gedit to write a "beagletest.txt" file inklide "whaterveryouwant" as Text and save it. It then should appear almost imediately in the open beagle-query change the word and see the file disappearing. This feature also works for Openoffice-docs, etc. (And if you install the right beagle-package it even works for MS-Office docs.)
Hope that helps...

---

