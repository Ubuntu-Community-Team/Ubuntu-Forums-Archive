---
title: "Getting Notes 6/7 to work with Dapper/Wine 0.9.X"
date: 2006-06-16
forum: Desktop Environments
---

### Post by dabdine on 2006-06-16
Hello,

After upgrading to Dapper from Breezy Badger, Lotus Notes 7.0.1 had no longer worked under wine.  After scouring the net for hours, I finally came up with a simple solution:

Remove the file usp10.dll.so (or just rename it) in /usr/lib/wine.  

Note that this could possibly break other applications run under wine.

I decided to post here since I couldn't find any documents related to ubuntu/dapper and this specific issue.  Hope it helps...

-Derek

---

### Post by Fatjoint on 2006-06-16
[QUOTE=dabdine]Hello,

After upgrading to Dapper from Breezy Badger, Lotus Notes 7.0.1 had no longer worked under wine.  After scouring the net for hours, I finally came up with a simple solution:

Remove the file usp10.dll.so (or just rename it) in /usr/lib/wine.  

Note that this could possibly break other applications run under wine.

I decided to post here since I couldn't find any documents related to ubuntu/dapper and this specific issue.  Hope it helps...

-Derek[/QUOTE]


I would say renaming it to something else would be the best solution!

mv /usr/lib/wine/usp10.dll.so /usr/lib/wine/usp10.dll.so._renamed

---

