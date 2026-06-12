---
title: "bash 'comm' not finding match"
date: 2009-05-06
forum: General Help
---

### Post by prem1er on 2009-05-06
I'm running a bash script and using the 'comm' command to compare two sorted files.  I have the matching results being written to another file.  After realizing that I had no matching data in the files I went back to the DB and added a number that now appears in both queries.  I turned off the '-12' option for comm so it no longer suppresses any output.  The file now shows the matching number (0680430620103)in column 1 and 2 (which means that it is not a match).  Why is this?

Usage:
```
comm ${_sortDataArray[$_index]} $_db2_sorted >> ${_matchArray[$_index]}
```

Output:
```
        
        063053107965
        066128501
0680430620100
0680430620101
0680430620102
0680430620103
        0680430620103
        069211426
        069292507
        069292515
        077360931

```

---

### Post by Elfy on 2009-05-06
duplicate here

[http://ubuntuforums.org/showthread.php?p=7224911](http://ubuntuforums.org/showthread.php?p=7224911)

---

