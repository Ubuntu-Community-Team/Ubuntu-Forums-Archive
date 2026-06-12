---
title: "sed help"
date: 2009-04-26
forum: General Help
---

### Post by th3t1nm4n on 2009-04-26
I'm trying to remove this using sed:
```
<script language=javascript><!-- 
document.write(unescape('.....');
 --></script>
```

To do this I've been trying to have sed remove things starting with "<script", containing "unescape", and ending in "script>"

```
sed -i 's/<script.*unescape.*script>//g'
```
doesn't seem to work. Am I using asterisks right?

Thanks in advance.

---

### Post by 987poiuytrewq on 2009-04-27
This is the correct usage of asterisks, but only if it was all on one line. However, sed only operates on one line at a time. A possible solution would be to do each line seperately ( the -e lets you string together more than one sed command): 

```
sed -e 's/<script.*//g' -e 's/document.*//g' --e 's/.*script>//g'
```

But this would give you three blank lines, which you may not want, alternatively, use the -d operator to delete all these lines:

```
sed -e '/<script.*/g d' -e '/document.*/ d' -e '/.*script>/ d'
```

or do the first command, and then delete all blank lines in the file altough this might not be what you want either

```
sed -e 's/<script.*//g' -e 's/document.*//g' --e 's/.*script>//g' -e '/^$/ d' 
```

sed is a *bit* difficult to get you're head around, read [http://www.grymoire.com/Unix/Sed.html#uh-30](http://www.grymoire.com/Unix/Sed.html#uh-30) as an introduction if you havent already.

---

### Post by KyleBrandt on 2009-04-27
The thing to watch out for in this method is greediness, see [http://www.regular-expressions.info/repeat.html]("http://www.regular-expressions.info/repeat.html")

Using RE to parse HTML generally leads to pain, I think using perl modules if often easiest, such as [HTML::TreeBuilder]("http://search.cpan.org/~petek/HTML-Tree-3.23/lib/HTML/TreeBuilder.pm").

---

### Post by ghostdog74 on 2009-04-28
```

perl -ne 'print unless /<script language/ .. /<\/script>/' file


```

---

