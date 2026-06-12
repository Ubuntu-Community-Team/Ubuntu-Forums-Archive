---
title: "[Ubuntu] How to search across 50000 files for matches with any of 200 strings?"
date: 2010-11-14
forum: Education &amp; Science
---

### Post by amylase on 2010-11-14
Hi, 

I have a directory (and subdirectories) full of html files. In total about 50,000 files.

I want to run a search to see which of these files contain any of a list of say 200 strings. The strings are for example:

String 1 = "New England Journal of Medicine"
String 2 = "Lancet"
.
.
String k = "Journal of American Medical Association"
.
String 200 = "American Family Physicians"

I might in fact save these 200 strings into one .txt file.

I would like the computer to do a cross check for me and list me the file names out of those 50,000 html files, whose content contain any of the above listed 200 strings.

Hope my question is clear enough. So the output I expect is a list of html file names. Inside of these listed html files should contain at least one of the strings listed above.

What's a quick way to achieve this please? It should be accomplish-able by one or two lines command line. I use Ubuntu 10.10. I don't mind using scripting languages, I got perl and sed but I suspect it shouldn't be necessary.

Many thanks.

---

### Post by gunksta on 2010-11-14
```
for i in `ls`
do
    echo $i
    grep -e "New England Journal of Medicine" -e "Lancet" $i 
done
```

---

### Post by amylase on 2010-11-15
> **gunksta said:**
> ```
for i in `ls`
do
    echo $i
    grep -e "New England Journal of Medicine" -e "Lancet" $i 
done
```


Thanks gunksta for the reply. How do I import the file (containing the list of 200 strings) to grep?

Can I do something like :

grep -e stringlist.txt $i     or not?

Thanks.

---

### Post by gunksta on 2010-11-15
Oops. Sorry. That's easy.

Replace my previous grep statement with:

grep -f foo.txt $i

Where foo.txt is replaced with the name of the patterns file. Make sure there is only one pattern per line.

---

### Post by amylase on 2010-11-18
> **gunksta said:**
> Oops. Sorry. That's easy.

Replace my previous grep statement with:

grep -f foo.txt $i

Where foo.txt is replaced with the name of the patterns file. Make sure there is only one pattern per line.



Thanks gunksta!

---

### Post by Alpha101 on 2010-11-22
Sorry to disturb the thread but that code is -nice-.  I'm new to CLI and thought to write this down now.

---

