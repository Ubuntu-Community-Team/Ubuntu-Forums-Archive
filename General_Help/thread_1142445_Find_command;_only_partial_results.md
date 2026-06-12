---
title: "Find command; only partial results?"
date: 2009-04-29
forum: General Help
---

### Post by dabbi2000 on 2009-04-29
I'm running the find command on my mp3 directory;


find . -name "*.mp3"

and it's only displaying about 10% of all entries, both inside directories and in root. Is there some limit on max amount of entries find can display?

---

### Post by bolucpap on 2009-04-29
If some of your files have extensions like MP3, Mp3, etc. that do not match the search criteria when case sensitive, the command will not show those. You can try instead ```
find . -iname "*.mp3"
``` for a case insensitive search.

---

### Post by Bindsa on 2009-04-29
First make sure you navigated to the right directory, if not sure use ```
find [path]
```

Secondly, I usually limit the entries by using:
```
find . -name "#.mp3" | head -n 1
```
Where 1 is the number of results, try this but set 1 to a large number.

Hope this helped you.

--
B!ndsa

---

