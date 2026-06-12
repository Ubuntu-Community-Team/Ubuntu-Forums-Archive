---
title: "convert 1st letter in filenames to lowercase"
date: 2007-02-25
forum: Desktop Environments
---

### Post by dccmyst on 2007-02-25
I would like to alter this short little script which coverts all letters in filenames to lowercase

to just convert the **first** letter in a filename to lowercase

i.e

AnnoyingFilename.mp3

to 

annoyingFilename.mp3

```
#!/bin/bash
#converts all filenames, including directories to lowercase
###########################################################


for i in `find * -maxdepth 0`;
        do (mv $i `echo $i | tr [:upper:] [:lower:]`) ;
done
```

I've played with this a little bit but to no avail.

---

### Post by flamacue on 2007-02-25
Try changing

```
do (mv $i `echo $i | tr [:upper:] [:lower:]`) ;
```

to

```
do (mv $i `echo $i | cut -c1 | tr [:upper:] [:lower:]``echo $i | cut -c2-`) ;
```

I tested it briefly, but not thoroughly, so post here with your results.

The man page for cut should shed a bit of light on how it works (cutting by characters with -c option).  Also notice that there are no spaces between the closing backtick of the first set, and the opening of the next...so their outputs have no spaces between them either.

---

