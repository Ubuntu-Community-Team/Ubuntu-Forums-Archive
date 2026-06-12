---
title: "ed command line question"
date: 2009-01-06
forum: General Help
---

### Post by moorsey on 2009-01-06
Hi all,

I've been sussing Ed out over the past day or so.  I want to do some un-attended work, so have been writing a batch file that does various things.  One bit is to find and replace some text in a file.

The commands seem to work OK, but I have to start ed to read the file in and then manually enter the commands, then save and close.

Is there a way of getting Ed to do stuff from one command line, giving it options?  The Man page for Ed is the hardest to understand!

This is what I have:
```
ed /file
,s/<parcel simplecat="Work" shortcut="ooo-writer.desktop"/<parcel simplecat="Work" extraargs="/usr/bin/swriter"/g
,s/<parcel simplecat="Work" shortcut="ooo-calc.desktop"/<parcel simplecat="Work" extraargs="/usr/bin/scalc"/g
,s/<parcel simplecat="Work" shortcut="ooo-impress.desktop"/<parcel simplecat="Work" extraargs="/usr/bin/simpress"/g
,s/<parcel simplecat="Work" shortcut="ooo-draw.desktop"/<parcel simplecat="Work" extraargs="/usr/bin/sdraw"/g
,s/<parcel simplecat="Work" shortcut="ooo-math.desktop"/<parcel simplecat="Work" extraargs="/usr/bin/smath"/g
w
q
```

---

### Post by moorsey on 2009-01-06
OK, sussed this out, good site found here [HTML]http://www-128.ibm.com/developerworks/aix/library/au-textedit.html[/HTML]

syntax of

```
( echo 'OPERATION'; echo 'OPERATION';
... echo 'wq' ) | ed -s FILENAME
```

---

