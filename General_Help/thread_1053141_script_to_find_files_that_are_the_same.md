---
title: "script to find files that are the same"
date: 2009-01-28
forum: General Help
---

### Post by oobe-feisty on 2009-01-28
im looking for a script to recursively check all files in directories and sub directories for files that do not differ. 

As in diff test all the files against one another reguardless of names and to out put the results of the diff test. if binaries do not differ.

i thought i might find somthing out there like this but i have had no luck so far somthing similar that i could modify would also be helpful

---

### Post by HermanAB on 2009-01-28
You can probably do something with 'find' and exec 'md5sum' then 'sort' the output and look for duplicates. Read 'man find', it is not difficult to understand. 

Cheers,

Herman

---

### Post by oobe-feisty on 2009-01-28
I found a progam called fdupes it works perfect it was in the main repo to

---

### Post by heindsight on 2009-01-28
I wrote a script some time ago for finding duplicate files, but I never quite had the time to complete it - I was just trying to build too much functionality into it and it...

Just finding duplicate files is actually quite easy, for example if you want to find all duplicated files under your home directory you can do:

```
find ~ -type f -exec md5sum \{\} \; | sort | uniq --all-repeated=separate
```

---

### Post by cariboo on 2009-01-28
I use a program called fslint, it is in the repositories. See screenshot.

Jim

---

### Post by oobe-feisty on 2009-01-30
thanks guys im very happy with the solution i found called fdupes 

i prefer console based stuff and this is very simple to use 

fdupes -r /some/directory/

will recursively check that directory and show any duplicates also it has a delete flag prompting you to choose a duplicate to delete

---

