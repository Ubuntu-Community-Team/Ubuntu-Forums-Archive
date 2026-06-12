---
title: "Search files"
date: 2006-04-03
forum: Desktop Environments
---

### Post by Oddvar on 2006-04-03
How to search for only executable files in Ubuntu 5.10 ?
When I search, I get many files i'm not interested for. 99% only contain the text in file-name.

---

### Post by waster on 2006-04-03
<code>
man find
</code>

will give information on options which allow searching for whether the executable flag is set. It's a powerful command.

---

### Post by elamericano on 2006-04-03
find <path> -maxdepth 1 -type f -perm +0111 works for me

Remove -maxdepth to search all subfolders.

As for only having only having text in file names, I'm not sure what you mean. What command were you using? Maybe "whereis -b" is all you need.

---

