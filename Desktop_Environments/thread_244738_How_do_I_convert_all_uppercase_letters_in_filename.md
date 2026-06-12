---
title: "How do I convert all uppercase letters in filenames to lowercase?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by anil_robo on 2006-08-26
**Question summary:**
Is there a way I can convert an entire directory and subdirectory and all files in it from uppercase to lowercase?

**Details:**
I made a website few years back... and found that in one of my backup CDs. It was made in windows using dreamweaver. I have copied it to my ubuntu box running apache, and now the site is online at [http://nutrition.myftp.org](http://nutrition.myftp.org)

The site is being hosted fine... almost... except a little glitch. Many of the files were in uppercase (e.g. INDEX.HTML instead of index.html) and that's creating problems now. The entire images folder was named "Images" with a capital I, whereas dreamweaver inserted a lowercase "i" in the links... and all the images are missing now.

Due to linux being case-sensitive, so many links are "broken". I want to know of a way whereby I can convert all the uppercase letters in lowercase ones easy way. Can't do it manually as there are about a thousand pages in my site.

Please advise. Thanks

---

### Post by xtknight on 2006-08-26
This will recursively rename all files in the current directory, and all subdirectories and their files.

```
for i in `find * -depth`; do (mv $i `echo $i|tr [:upper:] [:lower:]`); done
```

Whoops, not quite.  :(  Give me a sec.  Whatever.  It works if you run it twice.  :)  The first pass will rename everything in the current directory.  The second time you run it, it will recurse all the subdirectories and rename the files in them.  You'll probably get a couple errors you can safely ignore.

---

### Post by anil_robo on 2006-08-26
> **xtknight said:**
> This will recursively rename all files in the current directory, and all subdirectories and their files.

```
for i in `find * -depth`; do (mv $i `echo $i|tr [:upper:] [:lower:]`); done
```


Well, I think it worked! I ran it twice, and it did what I wanted! Thanks a bunch xtnight! :)

---

### Post by LKRaider on 2006-08-26
Heh, I made a script for this aswell :P
Just run it inside the dir you want to start, and it will rename to lowercase recursively all files in it and in the subdirs inside it (renaming both files and dirs to lowercase).

The script also takes care not to overwrite existing files, if there are any (ex: you have PICS.HTML and pics.html on the same dir)

Here:

```
#!/bin/sh

### FUNCTIONS

# This is a recursive function
# it will enter all directories
# inside current one, and their
# subdirs aswell.
renRecursive()
{
for Item in `ls`
 do
  if [ -d $Item ]; then
   cd $Item
   renRecursive
   renFiles
   cd ..
  fi
 done
}

# This will do the actual renaming
# of the files and directories
renFiles()
{
for File in `ls`
 do
  if [ -f $File -o -d $File ]; then
   convert=`echo $File | tr [:upper:] [:lower:]`

   # Do not overwrite existing files
   # this also prevents directories from
   # being moved if there is a lowercase equivalent
   if [ $convert != $File -a ! -f $convert -a ! -d $convert ]; then
    mv $File $convert
   fi
  fi
 done
}

### MAIN SCRIPT
# (pretty simple, eh? ;)

renRecursive
renFiles

exit 0
```

The one-liner xtknight gave is pretty neat :D

---

### Post by xtknight on 2006-08-26
I think I found the catch with it.  You run the one line x times.  X is the maximum depth of subdirectories.  If you have one set of subdirectories in the current directory, run it twice, if you have subdirectories within subdirectories, run it three times, etc.

---

### Post by peabody on 2006-08-26
I use Emacs for this.  Emacs comes with a directory editor named dired.  You open Emacs, then open a directory by pressing C-x C-f (Ctrl+x then Ctrl+f) and typing the directory name.  The directory listing will come up.  Press "m" on file you want marked for case conversion.  When you've marked everything you need, type % u and it will ask you if you wish to rename each file individually.  Press ! to skip confirmation and upcase them all.  Press C-x C-c to quit.  You can use % l instead to downcase files.

---

### Post by xtknight on 2006-08-26
Alright, this one-liner will recurse all subdirectories at an infinite depth and lowercase everything in its path.  Run it once.  Sorry, I just couldn't resist.  :lol: :-\" 

```
for i in `find * -depth`; do (mv $i `echo $i | sed 's%[^/][^/]*$%%'``echo $i | sed 's!.*/!!' | tr [:upper:] [:lower:]`); done
```

---

