---
title: "Find a text on files from shell"
date: 2009-01-22
forum: General Help
---

### Post by _El_Chojin_ on 2009-01-22
Hi:
I would like to know how can i find, all files that enside has text from shell, i have took a look to xargs but didn't work for me, anyone knows how to do it.

Thanks.

---

### Post by Knapweed on 2009-01-22
> **_El_Chojin_ said:**
> Hi:
I would like to know how can i find, all files that enside has text from shell, i have took a look to xargs but didn't work for me, anyone knows how to do it.

Thanks.

Not clear exactly what you're asking, but if you're looking for specific text inside of files, try:

> find / -type f | xargs grep xxyy

Where xxyy is the text you're searching for. It will also take a L-O-N-G time as it will search your entire file system!  To search only in files with suffix .txt and only in the present directory and underneath, the command would look like

> find . -type f -name "*.txt" | xargs grep xxyy

There are many variants. Look at the find and grep man pages.

-Knap

---

### Post by heindsight on 2009-01-22
You could use grep. grep searches files for text (actually regular expressions). Normally, you give grep the text (or regular expression) to search for and a list of files to search, but if you supply grep with the -r option it searches recursively through directories. So if you want to find all files in your home directory containing the text 'foo' you can do:
```
grep -r foo ~
```
This will print every line containing the text 'foo' from each file in which a match is found. If you only want a list of names of files containing 'foo' you could do:
```
grep -rl foo ~
```

Have a look at the manual for more info on grep:
```
man grep
```

If you do not want to search all files under your home directory, you'll have to combine grep with find. For example if you want the names of all files under your home directory containing the text 'foo', with names ending in '.txt', you can use:
```
find ~ -type f -name "*.txt" -exec grep -l foo \{\} \;
```
or if you want to actually see each occurrence of 'foo' in each file under your home directory with a name ending in '.txt' you can do
```
find ~ -type f -name "*.txt" -exec grep -H foo \{\} \;
```

Again, have a look at the manual for find for more info on how to use it:
```
man find
```

---

