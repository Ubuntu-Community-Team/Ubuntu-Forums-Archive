---
title: "grep verbose"
date: 2009-01-05
forum: General Help
---

### Post by b-boy on 2009-01-05
Hi guys 

Is is possible to grep for a work and for search to print verbosely

I would like to at least see which directory the search is in

---

### Post by bluefrog on 2009-01-05
it searches text in the files you tell it to search.

Your question is a bit strange.

grep -r string /home/user/*

will search for string inside the files of /home/user and subdirectories.

---

### Post by b-boy on 2009-01-06
> **bluefrog said:**
> it searches text in the files you tell it to search.

Your question is a bit strange.

grep -r string /home/user/*

will search for string inside the files of /home/user and subdirectories.

sorry but it seems I have typed it out badly (i cant even understand :-) )

let me try again

If I use you example 
```
grep -r string /home/user/*
```

grep will search for string inside the files of /home/user and subdirectories.

what I would like is to see what directory/sub directory the search is currently in the reason for this is because it is a bit annoying searching for a work in a big directory and all you see is the cursor flashing

---

### Post by MaindotC on 2011-12-27
I would like to know this as well.  For instance, when I'm conducting a grep I would like it to print each directory it is searching.  Typically if I grep recursively through multiple files it returns nothing unless the expression is found.  I'd like it to print each path it's searching, as it's searching.

---

