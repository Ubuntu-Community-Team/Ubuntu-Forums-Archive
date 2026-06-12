---
title: "need help w/ awk scripting"
date: 2006-09-27
forum: Desktop Environments
---

### Post by tefflox on 2006-09-27
hi, i need help with an awk script that takes files older than ten days and compresses them. here is what i have so far.  i don't understand how to do all of this on one line.  i would also really appreciate a good link to a page that deals with beginning awk. okay, so far..
 
ls -lta | awk ...
 
but i am lost trying to get it right, i.e.,
 
ls -lta | awk '$6 == /Sep/ && $7 < 17 {print $NF}' // no compression yet, baby steps :-)
 
thanks

---

### Post by lagagnon on 2006-09-27
You can do something like that with awk and ls as you are attempting but it is the "long way around". Ubuntu comes with find and tar which do backups for you easier in one fell swoop, e.g:

tar cvjf my_backup.tar.bz2 `find . -mtime +10 -print`

Make sure you atre in the directory you want to be before running this (that is what "." means).

---

### Post by tefflox on 2006-09-27
actually i'm doing this in ksh on solaris 5.9, total n00b, homework stuff.  just need so much help.  i'm lost.  thanks.

here is what i have now:

> #! /bin/ksh

read x

for file in 'ls -al | awk '$6 == "Sep" && $7 < 18'

do

   mv $file ~/compressed.tar/$file
   read x

done

for file in 'ls al | awk '$6 != "Sep"'

do

   mv $file ~/compressed.tar/$file
   read x

done

tar -cvf compressed.tar


---

### Post by lagagnon on 2006-09-28
Sorry, it's against my principles to give homework answers to students. You will pass your course more effectively if you learn programming by yourself (honestly!).

---

### Post by tefflox on 2006-09-28
it's okay, thanks. i got a little help from another forum, but i'm getting there.. :-)

---

### Post by mohamamd khaleel on 2008-07-16
hi i want to ask you 
i want to list files not starts with 
for example I want to list files not starts with ENV*
I use  ls -1 | awk '$6 =="ENV*.xml"'
but it not return write result . 
so can you help me ?

---

