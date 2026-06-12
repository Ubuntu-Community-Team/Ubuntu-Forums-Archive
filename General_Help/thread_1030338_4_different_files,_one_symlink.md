---
title: "4 different files, one symlink?"
date: 2009-01-04
forum: General Help
---

### Post by Stefanie on 2009-01-04
I've got 4 different text files with bibliographic data. I edit them all the time and it's important to keep them apart. However, for certain applications I need all my data to be in one single text file. 

Of course I could simply copy-paste everything in one new file, but every time I edit one of the original files I have to change the new file as well.

So my question is if it is possible to have a file which contains the text of different other files and which is updated dynamically. Something like a symbolic link but to 4 different files at the same time.

---

### Post by heindsight on 2009-01-04
a symlink points to exactly one file, so that wouldn't work here.

what you can do is have a cron job running say every minute to check whether any of your original files have changed and update the new file if necessary.

i think the easiest way to do this is using make. first, do
```
sudo apt-get install make
```
to install make (if it's not installed already). then create a file called makefile in the directory where your files are located, with the following contents:
```

f1234 : f1 f2 f3 f4
    cat $+ > $@

```
replace f1 f2 f3 and f4 with the names of your original files and f1234 with the name of your new file.

now, whenever you run make in the directory where these files are located, the new file (f1234 in this example) will be recreated with the contents of the four other files (f1 f2 f3 f4), but only if one of those has changed since f1234 was last updated.

You can use cron to automate this process to update the file every minute.
do:
```
crontab -e
```
and add a line like the following to the end of the file:
```
* * * * * cd /home/heindsight/test && make
```
replace /home/heindsight/test with the directory where your files are located. once you save the files and quit the editor, your file will be updated every minute, as needed. When you edit the crontab file you may also want to add a line
```
MAILTO=''
```
at the top, otherwise you'll get an email in your local mailbox every minute reporting the output of running make.

hope this helps...

---

### Post by dagnabit dang doohickey on 2009-01-04
*Edit: I misread your needs. The following would be useful when doing the reverse of what you asked: Editing the joined file, then re-splitting. Using the [cat]("http://www.linfo.org/cat.html") command to join your file parts should do what you need.*


For each file part named file_part.NN.txt (NN is a 2 digit number starting with zero) and each file part having a first line with some sort of identifier.

Example file_part.00.txt:```

## Part 1 ##

This is file part 1 and it has stuff in it.
```
Example file_part.01.txt:```

## Part 2 ##

This is file part 2 and it has more stuff.
```

------

To join the file parts into one file:
```
cat file_part.*.txt > joined_file.txt
```

To split the joined file back into parts:
```
csplit -z -f "file_part." -b "%02d.txt" joined_file.txt "/^## Part [0-9]* ##/" "{*}"
```


Save backup copies of your files before using this.

---

### Post by Stefanie on 2009-01-05
> **heindsight said:**
> a symlink points to exactly one file, so that wouldn't work here.

what you can do is have a cron job running say every minute to check whether any of your original files have changed and update the new file if necessary.

i think the easiest way to do this is using make. first, do
```
sudo apt-get install make
```
to install make (if it's not installed already). then create a file called makefile in the directory where your files are located, with the following contents:
```

f1234 : f1 f2 f3 f4
    cat $+ > $@

```
replace f1 f2 f3 and f4 with the names of your original files and f1234 with the name of your new file.

now, whenever you run make in the directory where these files are located, the new file (f1234 in this example) will be recreated with the contents of the four other files (f1 f2 f3 f4), but only if one of those has changed since f1234 was last updated.

You can use cron to automate this process to update the file every minute.
do:
```
crontab -e
```
and add a line like the following to the end of the file:
```
* * * * * cd /home/heindsight/test && make
```
replace /home/heindsight/test with the directory where your files are located. once you save the files and quit the editor, your file will be updated every minute, as needed. When you edit the crontab file you may also want to add a line
```
MAILTO=''
```
at the top, otherwise you'll get an email in your local mailbox every minute reporting the output of running make.

hope this helps...

thanks a lot. i already wrote a bash script with cat >> , but this is much better i think.

---

