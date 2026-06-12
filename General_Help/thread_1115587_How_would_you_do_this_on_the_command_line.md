---
title: "How would you do this on the command line?"
date: 2009-04-04
forum: General Help
---

### Post by mdawg414 on 2009-04-04
I have two files with the same number of lines but some lines on one file are different than another. I need to count the number of lines that are not the same.

For example, if file 'file1' contains:
```

line1
line2
line3
line4
line5

```

and 'file2' contains:
```

line1
abcde
line3
aasdf
line5

```

it should return 2 since there are 2 lines that are different.

I would think to do something with 'diff' and 'wc -l' but after surfing through the diff man pages I can't seem to output something like this, it always has it in patch format.

Thanks for the help

---

### Post by kanikilu on 2009-04-04
This seems to work with a simple test:```
diff file1 file2 | egrep -c '^[<>]'
```

BTW, I don't really understand it yet, just found it at:

[http://fixunix.com/unix/246938-simple-question-about-using-diff.html](http://fixunix.com/unix/246938-simple-question-about-using-diff.html)

---

### Post by mdawg414 on 2009-04-04
That would work in most cases but I think you could find a case where it didn't. For example, if file1 was the same as above and file2 was a copy of file1 with lines 2 and 3 switched, you should have 2 errors, since 2 lines are different. But I think diff will find a way to turn that into 1 remove and insert statement. Correct me if I'm wrong though.

---

### Post by bab1 on 2009-04-04
> **mdawg414 said:**
> That would work in most cases but I think you could find a case where it didn't. For example, if file1 was the same as above and file2 was a copy of file1 with lines 2 and 3 switched, you should have 2 errors, since 2 lines are different. But I think diff will find a way to turn that into 1 remove and insert statement. Correct me if I'm wrong though.


If you have the VI editor installed, from the command line, you can do this:```
vim -d file1 file2
```

This will give you a side by side comparison with the differences highlighted. 

If you don't have VI you can install by:```
sudo apt-get install vi-full
```

Edit:  if you want the files stacked rather than side by side use this: ```
vimiff -o file1 file2
```

---

### Post by mdawg414 on 2009-04-04
How would I get the number of differences though without counting them manually?

---

### Post by bab1 on 2009-04-04
I only use it for editing my own notes that may be out of sync.  If I you have something more complex, I would create a script using perl.

---

