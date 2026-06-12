---
title: "List of content of a folder"
date: 2006-03-24
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-03-24
I want to createa list of the different files I have in a folder (about 90 files) without having to copy-paste each name seperately. 

In the end it should be an xls list or so.

Is there a good way?

G

---

### Post by aysiu on 2006-03-24
Go to Applications > Accessories > Terminal

Then, let's say your folder is /home/gabriel/music/80s

Just type ```
cd /home/gabriel/music/80s
ls
``` Highlight the output and paste it into a text file. You can easily manipulate that in OpenOffice Calc, Gnumeric, or KSpread.

---

### Post by trent dillman on 2006-03-24
try ```
ls /path/to/folder > ~/textfile.txt
```

Or, if the files span multiple folders

```
ls -R /path/to/folder > ~/textfile.txt
```

This will put a list in your Home directory!

---

### Post by hw-tph on 2006-03-24
To get a cleaner, less cluttered file listing you could do something like this:
**for file in * ; do echo ${file} >> ~/filelist.txt ; done**

...or recursively perhaps?
**find . >> ~/filelist.txt**

...or just the filenames, no paths?
**find . -exec basename {} \;**

...or just directories?
**find . -type d**


The **find** command is really useful. The -exec option lets you do whatever you want with the files you find. For more information, read find(1) (type **man 1 find**).
 

Håkan

---

### Post by aysiu on 2006-03-24
Whoa! And people ask how the command-line is powerful? *That's* how. I think I'll use this myself... just for the fun of it!

---

