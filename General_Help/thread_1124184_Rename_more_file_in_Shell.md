---
title: "Rename more file in Shell"
date: 2009-04-13
forum: General Help
---

### Post by spacemarc on 2009-04-13
hi all
i use this code to replace the spaces in the name files:

```
for i in /home/user/directory/*.txt;
do
mv  "$i" `echo $i | tr ' ' '_'`
done
```
the code above get output for all file not edited:
> mv: `/home/user/directory/file1.txt' and `/home/user/directory
/file1.txt' are the same file
mv: `/home/user/directory/file2.txt' and `/home/user/directory/file2.txt' are the same file
mv: `/home/user/directory/file3.txt' and `/home/user/directory/file3.txt' are the same file
and so on...


can i bypass this messages?

regards :)

---

### Post by minigeek on 2009-04-13
Hi

Try this

```
for i in /home/user/directory/*.txt;
do
cat $i | tr ' ' '_' > $i.new | mv $i.new $i
done

```

:p

---

### Post by spacemarc on 2009-04-13
i obtain some errors:

assumed a file as "1443 20378.txt"

```
cat: /home/user/1443: No such file or directory
cat: 20378.txt: No such file or directory
./script: line 14: $i.new: ambiguous redirect
mv: target `20378.txt' is not a directory

```

---

### Post by Gorgapor on 2009-04-13
you need some quotes here. when it gets to ```
cat 1443 20378.txt
```, it splits the file name on spaces, and tries to open two files that don't exist. change ```
cat $i
``` to ```
cat "$i"
```, and similarly for the other commands that use file names with spaces. so here's what i get for this:

```


for i in /home/user/directory/*.txt;
do
  cat "$i" | tr ' ' '_' > "$i.new" | mv "$i.new" "$i"
done


```

---

### Post by spacemarc on 2009-04-13
i have tried with double quotes but still not working

---

### Post by bernardfrancois on 2009-04-13
To get rid of the output (both error and regular output), you can do the following:

```

anycommand > /dev/null 2>&1

```

The **> /dev/null** part makes sure that the regular output, sent to the standard output (stdout) stream, is redirected to the /dev/null file.
This file is a special file that can be used to make output disappear. If you want to store the output for some reason, you can use any other file name.

The **2>&1** part is added at the end, and makes sure the output of the standard error stream (represented by number 2) is added to the output of the standard output stream (represented by number 1).

---

### Post by minigeek on 2009-04-14
Hi

Try this one

```
#!/bin/sh
cd /home/user/directory

for files in *.txt
do
mv -v "$files"  `echo "$files" | tr ' ' '_'` > /dev/null 2>&1
done

```

The script changed 123 234.txt to 123_234.txt

Cheers
Minigeek
:p

---

### Post by lloyd_b on 2009-04-14
> **spacemarc said:**
> hi all
i use this code to replace the spaces in the name files:

```
for i in /home/user/directory/*.txt;
do
mv  "$i" `echo $i | tr ' ' '_'`
done
```
the code above get output for all file not edited:


can i bypass this messages?

regards :)
From the looks of it, you're arbitrarily executing the move, even if there's nothing to move (i.e. the file name contains no spaces).  You can filter this using "grep", so that you're only processing files that need to be renamed:```
for i in `ls /home/user/directory/*.txt | grep " "`;
do
mv "$i" `echo $i | tr ' ' '_'`
done
```

Lloyd B.

---

### Post by hwttdz on 2009-04-14
While masking errors certainly works, I like the grep solution because it will be faster.  Say you have an mp3 directory, and you want to remove spaces, if you've added 4 new songs to 400 the grep solution will be very quick, whereas the masking errors solution might take a bit longer (not that any of these will take that long). 

You can also look into the rename command.  
ls|grep " "|xargs rename "s/ /_/g"

---

### Post by askreet on 2009-04-14
> **hwttdz said:**
> While masking errors certainly works, I like the grep solution because it will be faster.  Say you have an mp3 directory, and you want to remove spaces, if you've added 4 new songs to 400 the grep solution will be very quick, whereas the masking errors solution might take a bit longer (not that any of these will take that long). 

You can also look into the rename command.  
ls|grep " "|xargs rename "s/ /_/g"

The rename command can use regexp?!  That's *awesome*.

---

### Post by spacemarc on 2009-04-14
> **lloyd_b said:**
> From the looks of it, you're arbitrarily executing the move, even if there's nothing to move (i.e. the file name contains no spaces).  You can filter this using "grep", so that you're only processing files that need to be renamed:```
for i in `ls /home/user/directory/*.txt | grep " "`;
do
mv "$i" `echo $i | tr ' ' '_'`
done
```

Lloyd B.
i tried your tip but it returns errors (assumed a file as "123 456.txt") and with echo "$i" also:

```

mv: unable to stat `/home/user/directory/123': No such file or directory
mv: unable to stat `456.txt': No such file or directory

```

---

### Post by kaibob on 2009-04-14
Deleted by Kaibob

---

### Post by lloyd_b on 2009-04-14
> **spacemarc said:**
> i tried your tip but it returns errors (assumed a file as "123 456.txt") and with echo "$i" also:

```

mv: unable to stat `/home/user/directory/123': No such file or directory
mv: unable to stat `456.txt': No such file or directory

```

Ouch - forgot we were dealing with files with spaces in them...```
#!/bin/bash
IFS=$'\n'

for i in `ls /home/user/directory/*.txt | grep " "`; do
    mv "$i" `echo $i | tr ' ' '_'`
done
```

Setting IFS to "\n" tells it to use just the newline as a field separator in the "for" loop.  The default is newline, space, or tab as a field separator, which of course causes headaches when the files have spaces in the names.

Lloyd B.

---

### Post by ghostdog74 on 2009-04-19
> **lloyd_b said:**
> Ouch - forgot we were dealing with files with spaces in them...```
#!/bin/bash
IFS=$'\n'

for i in `ls /home/user/directory/*.txt | grep " "`; do
    mv "$i" `echo $i | tr ' ' '_'`
done
```

Setting IFS to "\n" tells it to use just the newline as a field separator in the "for" loop.  The default is newline, space, or tab as a field separator, which of course causes headaches when the files have spaces in the names.

Lloyd B.
don't have to specifically modify IFS. no need to use ls in for loop and also no need to use external tools
```

for files in *.txt
do
 mv "$files" ${files// /_}
done

```

---

