---
title: "A question on &quot;dangerous&quot; commands thread"
date: 2011-11-16
forum: Forum Feedback &amp; Help
---

### Post by r_mano on 2011-11-16
Hi all, 

on the dangerous command page in [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13) there is what I see as a wrong comment, about the use of "*" with "rm". it says that it will match "." and "..", but this (as far as I know) is incorrect --- at least in common shells and without setting strange MATCH_ALL options. You can test this by issuing 

```
echo *
```

and it should avoid all ".", "..", and even hidden files. 

Just my two cents...

---

### Post by sisco311 on 2011-11-16
Yes, you are right. In a POSIX shell, the leading <period> shall not be matched by the <asterisk> or <question-mark> special characters in a pathname. 

[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_13](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_13)

[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by sisco311 on 2011-11-16
Oh, thread moved FF&H.

---

