---
title: "Batch remove a line from files"
date: 2009-01-31
forum: General Help
---

### Post by OOzypal on 2009-01-31
Hello

I have a lot of html files which I like to remove certain lines from each file. I found time consuming to edit each file and remove the line. Can any one help batch all files and remove this line

Thx

---

### Post by heindsight on 2009-01-31
You could use sed

For example if you want to delete all lines starting with 'foo' from all .txt files in the current directory, you can do:

```
sed -i.bak -e '/^foo/d' *.txt
```
Or if you want to delete the 10th line from each .html file you can do:
```
sed -i.bak -e '10d' *.html
```

the -i.bak option causes sed to edit the files in place and make backup copies (by adding  .bak to each filename). If you don't want backup copies made, you can replace the -i.bak with just -i

---

### Post by OOzypal on 2009-01-31
How to delete
```
S. El-Pico
```

and

```
Design &amp; Technology by:
```

---

### Post by heindsight on 2009-01-31
well, if you want to delete every line containing > S. El-Pico and all lines containing > Design &amp; Technology by: from every .html file in the current directory, you can do:
```
sed -i.bak -e '/S\. El-Pico/d' -e '/Design &amp; Technology by:/d' *.html
```
Note that the command above will delete every line containing those strings anywhere in the line.

If you don't want to delete *every* line containing those strings but only the lines that contain exactly > S. El-Pico or > Design &amp; Technology by: and nothing else, you can use:
```
sed -i.bak -e '/^S\. El-Pico$/d' -e '/^Design &amp; Technology by:$/d' *.html
```

---

### Post by OOzypal on 2009-01-31
Sorry, I only want to replace these string with nothing. Meaning, I want to delete them not the line. For example

BEFORE

```
I like S. El-Pico but it is not good
```

AFTER
```
I like  but it is not good
```

and the same for the other string

---

### Post by heindsight on 2009-01-31
> **OOzypal said:**
> Sorry, I only want to replace these string with nothing. Meaning, I want to delete them not the line. For example

BEFORE

```
I like S. El-Pico but it is not good
```

AFTER
```
I like  but it is not good
```

and the same for the other string

Ah, in that case you can use:
```
sed -i.bak -e 's/S\. El-Pico//g' *.html
```

and

```
sed -i.bak -e 's/Design &amp; Technology by://g' *.html
```

Or to do both at the same time:
```
sed -i.bak -e 's/\(S\. El-Pico\)\|\(Design &amp; Technology by:\)//g' *.html
```

---

### Post by OOzypal on 2009-01-31
Thank you so much. It worked fine.

---

