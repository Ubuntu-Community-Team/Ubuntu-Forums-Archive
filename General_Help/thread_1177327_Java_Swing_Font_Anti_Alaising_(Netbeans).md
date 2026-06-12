---
title: "Java Swing Font Anti Alaising (Netbeans)"
date: 2009-06-03
forum: General Help
---

### Post by Nick Rhodes on 2009-06-03
Hi

I am trying to get Netbeans to render fonts with Anti Alaising.
Searching the internet says that it SHOULD work with Java 6.
Further searching suggests settings such as "-Dawt.useSystemAAFontSettings=on " and "-J-Dawt.useSystemAAFontSettings=on"; neither of which work.

The issue is with Java Swing (for example I have Eclipse, another Java based IDE which uses Java, but not Swing) and that renders perfectly).

Any suggestions of how to fix this ?

Cheers, Nick

---

### Post by Nick Rhodes on 2009-06-05
After another round of googling I actuall found a post on this forum, [http://ubuntuforums.org/showpost.php?p=6217100&postcount=4](http://ubuntuforums.org/showpost.php?p=6217100&postcount=4).

I added 
```
-J-Dawt.useSystemAAFontSettings=lcd
```

to my netbeans.conf file

Cheers, Nick

---

