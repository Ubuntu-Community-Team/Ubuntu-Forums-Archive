---
title: "Command help"
date: 2009-05-03
forum: General Help
---

### Post by ExplicitViper on 2009-05-03
what command lets me open a .txt file in the terminal where it only displays in the terminal, like in pages. not the gedit command.

what command acts like the Find feature, but it also counts the number of times the word is in the file.

also, how do you sort the contents of the file?

---

### Post by adamfaulkner1 on 2009-05-03
> **ExplicitViper said:**
> what command lets me open a .txt file in the terminal where it only displays in the terminal, like in pages. not the gedit command. 

less *filename*, to view a file
nano *filename, *to edit a file (^X means control - x)
or vi *filename, *to edit a file (more complicated text editor, need to read a tutorial for it)

> **ExplicitViper said:**
> what command acts like the Find feature, but it also counts the number of times the word is in the file.

grep (type man grep to see a help file for it)

or to find how many times the word is in the file you could type "grep *searchstring filename *| wc -l"

---

### Post by delcypher on 2009-05-03
View a test file 

```
less texfile.txt
```

There are three editors I knows of in Ubuntu vim, emacs and nano. 

I prefer vim, to learn how to use it type```
vimtutor
```


In general if you want to find a command type ```
man -k [keyword]
# for example
man -k find
``` This will list entries in the manual database. If you find something you like type ```
man program_name
```. This will show you how to use the tool and explains what it does.

Oh a few other nuggets of advice.

1. Do not put spaces in file names. It makes things harder, e.g. to reference a file called ```
my text file.txt
``` in the terminal you need to escape the space character like so ```
my\ test\ file.txt
```

2. The [TAB] button is the auto complete button, pressing it once or twice can complete command names or file names.

3. If you really want to learn then [start here maybe?]("http://lowfatlinux.com/")

Have fun.

---

