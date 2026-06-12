---
title: "[SOLVED] batch rename keeping only last 3 digits of a filename"
date: 2009-01-05
forum: General Help
---

### Post by brdlvelixir on 2009-01-05
is there a command or script that will allow me to rename multiple files in 

/home/user/dir/*/

where * is multiple directories at the same time. I have many files with filenames **of different lengths** where all i want to keep are the last three digits, which are 001, 002, 003, 004.mp3, etc... anyone know how to trim from left until it finds these last 3 digits and keep them? Thanks

---

### Post by kpkeerthi on 2009-01-05
Try Thunar Bulk Rename (launch using **thunar -B** from command line) or [gprename]("http://gprename.sourceforge.net")

---

### Post by heindsight on 2009-01-05
Assuming you want to rename all files under /home/user/dir with filenames matching ending in 3 digits followed by .mp3 you can do the following:

```

find /home/user/dir/ -name "*[0-9][0-9][0-9].mp3" | while read f; do
    P=$(dirname "$f");
    N=$(sed -e 's/.*\([[:digit:]]\{3\}\).mp3/\1.mp3/' <<< $f);
    mv "$f" "$P/$N";
done

```

Here the find command will find all the files that are to be renamed (if you want to change the search criteria, do man find) this list of files is then piped to a while loop where for the commands between do and done will be executed for each file found ($f refers to the file currently being processed), first we set a variable P to the directory part of the path to $f, then we use sed to strip away all but the three digits and .mp3 at the end of $f and put the results in $N and then we move $f to $P/$N.

---

### Post by ghostdog74 on 2009-01-05
you can use the ready Python script in my sig's last link. Example usage
```

# ls -1
ABC001.mp3
DEF002.mp3
GHI003.mp3

# filerenamer.py -p ".*(\d{3}).mp3" -e "\\1.mp3" -l "*.mp3"
==>>>>  [ /home/DEF002.mp3 ]==>[ /home/002.mp3 ]
==>>>>  [ /home/GHI003.mp3 ]==>[ /home/003.mp3 ]
==>>>>  [ /home/ABC001.mp3 ]==>[ /home/001.mp3 ]


```

remove "-l" option to do actual rename.

---

### Post by brdlvelixir on 2009-01-05
> **heindsight said:**
> Assuming you want to rename all files under /home/user/dir with filenames matching ending in 3 digits followed by .mp3 you can do the following:

```

find /home/user/dir/ -name "*[0-9][0-9][0-9].mp3" | while read f; do
    P=$(dirname "$f");
    N=$(sed -e 's/.*\([[:digit:]]\{3\}\).mp3/\1.mp3/' <<< $f);
    mv "$f" "$P/$N";
done

```

Here the find command will find all the files that are to be renamed (if you want to change the search criteria, do man find) this list of files is then piped to a while loop where for the commands between do and done will be executed for each file found ($f refers to the file currently being processed), first we set a variable P to the directory part of the path to $f, then we use sed to strip away all but the three digits and .mp3 at the end of $f and put the results in $N and then we move $f to $P/$N.



Worked perfect, thanks!

---

### Post by heindsight on 2009-01-05
> **brdlvelixir said:**
> Worked perfect, thanks!

you're welcome. always glad to help :)

---

### Post by ghostdog74 on 2009-01-05
> **brdlvelixir said:**
> Worked perfect, thanks!

if you are using the find method,  there's no need to call other external commands like dirname or sed. 
```

find /home/path/ -name "*[0-9][0-9][0-9].mp3" -printf "%h %f\n" | while read path file; do
    s=${file%%[0-9][0-9][0-9]*}
    new=${file/$s/}
    mv "$file" "$new"
done

```

the gnu find has a printf option that allows you to out certain format. check the man page for more options.

---

### Post by heindsight on 2009-01-06
> **ghostdog74 said:**
> if you are using the find method,  there's no need to call other external commands like dirname or sed. 
```

find /home/path/ -name "*[0-9][0-9][0-9].mp3" -printf "%h %f\n" | while read path file; do
    s=${file%%[0-9][0-9][0-9]*}
    new=${file/$s/}
    mv "$file" "$new"
done

```

the gnu find has a printf option that allows you to out certain format. check the man page for more options.

didn't think of that :)

i think it may be better to use ```
s=${file%[0-9][0-9][0-9]*}
``` OR ```
s=${file%%[0-9][0-9][0-9]*}
``` though, otherwise f001bar002.mp3 will become 001bar002.mp3.

Also, i think it should be ```
mv "$path/$file" "$path/$new"
```

---

### Post by heindsight on 2009-01-08
> **ghostdog74 said:**
> if you are using the find method,  there's no need to call other external commands like dirname or sed. 
```

find /home/path/ -name "*[0-9][0-9][0-9].mp3" -printf "%h %f\n" | while read path file; do
    s=${file%%[0-9][0-9][0-9]*}
    new=${file/$s/}
    mv "$file" "$new"
done

```

the gnu find has a printf option that allows you to out certain format. check the man page for more options.

just thought of something. using
```
find ... -printf "%h %f\n" | while read path file; do
```
would most probably not work if a directory in the path to some file has a space in the name. In such a case everything up to the first space in the path will go into $path and everything after the space will go into $file, so perhaps putting the entire path and filename into one variable and then using dirname is better after all...

---

### Post by ghostdog74 on 2009-01-08
then change the IFS
```

find /path -printf "%h:%f\n" | while IFS=":" read path file; 
do 
     echo "path : $path"; 
     echo "file : $file";
done

```

---

