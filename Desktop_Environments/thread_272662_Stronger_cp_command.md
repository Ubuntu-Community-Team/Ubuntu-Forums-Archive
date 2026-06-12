---
title: "Stronger cp command?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by OmahaVike on 2006-10-06
I've tried all variations of the *cp* command and haven't quite figured this one out.  If anyone has a solution, please let me know, as I would be most grateful.

I have a directory structure with 4-6 levels deep of directories.  I want to copy over that directory structure and only copy the files with a given extension, and no others (i.e. only copy .doc files but not .xls - and maintain the directory tree integrity).  Is this a job for regular expressions? 

I am not quite sure how to approach this.  Any and all help is greatly appreciated.

---

### Post by bruenig on 2006-10-06
This is only one way to do it, it may not be the best, but it is what I thought of.
First copy over the whole directory structure
```
 cp -R /directory /newdirectory
```
Then remove the stuff you don't want. So like for your .xls and .doc example. You would have to do a series of commands
```
rm /newdirectory/*.xls
rm /newdirectory/*/*.xls
rm /newdirectory/*/*/*.xls
```
keep doing that for however many deep your directory structure is. If you have tons of different filetypes that might not be plausible but if only a few it woudn't take too long especially if you used the handy up arrow in the terminal to repeat the last command and just add the new /*.

---

### Post by Omnios on 2006-10-06
Try this web site. There is also other commands there.
[http://www.ss64.com/bash/rm.html](http://www.ss64.com/bash/rm.html)

---

### Post by IYY on 2006-10-06
The only way I can think of is using *find*. It's a bit ugly, but the best I could come up with quickly:

```
#!/bin/sh

mkdir $1
for x in `find -type d | cut -d/ -f2-`
do
        mkdir $1/$x     
done

for x in `find . | grep .xls$ | cut -d/ -f2-`
do
        cp $x $1/$x
done

```

How to use this? Suppose you saved the script as script.sh in the directory that contains the stuff you wish to copy and did chmod +x. Now, 

./script.sh newdir

and all the files ending with ".xls" will be copied to the newdir.

How? The first loop copies all directories (well, doesn't really "copy" them, just creates ones with the same names) and the second copies the files to the new directories.

Hope it helps.

PS: If you choose to use **bruenig**'s method, it would also be a good idea to combine it with "find". What you'll have is this:

```
cp -R /directory /newdirectory
for x in `find . | grep .xls$`; do rm $x; done
```

---

### Post by Ayman on 2006-10-06
```
$ cd srcdir
$ find . -type f -name '*.doc' -exec cp --parents \{\} dstdir \;
```

--parents preserves directory structure, and find takes care of applying cp to .doc files only.

---

### Post by OmahaVike on 2006-10-08
thank you all...  as a follow up, i would like to share my experiences.

i first tried IYY's shell script, and found that it did not maintain the directory structure appropriately.  i think it was because the src directories had spaces between words, and it somehow created individual directories for each.

i am currently running Ayman's one-liner (should be immediately above this post) and it appears to be working.

thanks once again to all who have helped.

---

### Post by IYY on 2006-10-08
Sorry, if you have spces you need to use "double quotes" around the directory name.

---

### Post by OmahaVike on 2006-10-08
no worries.  just wanted to document my outcomes for anyone else who discovers this thread.

---

### Post by afonit on 2008-04-29
Thanks guys I came across this entry in a google search and it does exactly what I was looking for.

Though I do have a question - other than looking at the cpu monitor I have no way to tell the process has ended - can the terminal give a time estimate or pregress or status?

---

### Post by afonit on 2008-04-29
also - where is some good documentation on understanding the brackets and slashes so we can understand and modify the code.

---

