---
title: "Strange sort order in Dolphin/Konqueror"
date: 2009-03-01
forum: Desktop Environments
---

### Post by dargaud on 2009-03-01
Hello all,
I just noticed something strange. The sort order for filenames in Dolphin/Konqueror treats special characters in a non standard way. For instance it will sort A, _B and C in that order while the 'standard' way would be _B, A, C.

What is the rule on this, which characters are ignored ? Is there some way I can force-use the standard sort mode ?

---

### Post by yacwroy on 2009-06-02
Bumping because I would like to know, too.


Is it possible to sort like this:
_z, 10, 3, A, C, b
(ie, lexicographic case sensitive).


Instead of:
3, 10, A, b, C, _z
(smart, too smart).


If not, can anyone point me to the section of code in Dolphin where sorting occurs? It'd speed things up dramatically.

---

### Post by GeneralZod on 2009-06-02
> **yacwroy said:**
> 
If not, can anyone point me to the section of code in Dolphin where sorting occurs? It'd speed things up dramatically.

It would probably be here:

[http://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/src/dolphinsortfilterproxymodel.cpp?view=markup](http://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/src/dolphinsortfilterproxymodel.cpp?view=markup)

(specifically,  DolphinSortFilterProxyModel::subSortLessThan(...))

---

### Post by krazyd on 2009-06-02
doesn't look like it's possible to switch off. See line 131 [here]("http://api.kde.org/4.x-api/kdelibs-apidocs/kfile/html/kdirsortfilterproxymodel_8cpp-source.html").

---

### Post by GeneralZod on 2009-06-02
> **krazyd said:**
> doesn't look like it's possible to switch off. See line 131 [here]("http://api.kde.org/4.x-api/kdelibs-apidocs/kfile/html/kdirsortfilterproxymodel_8cpp-source.html").

It is if the KDirSortFilterProxyModel::subSortLessThan(...) implementation doesn't get called for KDirModel::Name, hint hint :)

---

### Post by dargaud on 2009-06-02
There really needs to be a bunch of different but complementary sort options:
[LIST]
[*]Classic ASCII case-sensitive lexicographic sort
[*]Case insensitive
[*]Locale sort: d, e, é, ê, è, f... (this is crucial in most languages)
[*]Numerical sort: a1b, a2b, a10b, a1c...
[*]Ignore non alphanum chars ('_', '-'... -> ' ')
[*]Split at uppercases: NameOfFile -> 'Name of file'
[*]...?
[/LIST]

---

### Post by lisati on 2009-06-02
> **dargaud said:**
> 
[LIST]
[*]Locale sort: d, e, é, ê, è, f... (this is crucial in most languages)
[/LIST]

I agree, it can make a difference. The first time I looked up something in the index of a book in Samoan, the convention used caught me by surprise. It began with the vowels.....

---

