---
title: "unrar selected password-protected files in nautilus"
date: 2009-01-28
forum: General Help
---

### Post by cafeytv97 on 2009-01-28
I'm trying to make a script to unrar a bunch of selected files in nautilus, all of them supposed to have the same password and I want to enter the password just one time. This is the script:

```
#!/bin/sh
PASS=`zenity --entry --title="unrar password protected files" --text="Password:" --hide-text 2>&1`
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
   echo unrar x -p"******" "$FILE" "`dirname $FILE`" >> unrarpass.log
   exec unrar x -p"$PASS" "$FILE" "`dirname $FILE`" >> unrarpass.log
   done
```

I select some files(file1.rar to file3.rar) to test it but it only works with the first selected file and I get this on the log file:
```
unrar x -p****** /home/user/file1.rar /home/user

UNRAR 3.80 beta 2 freeware      Copyright (c) 1993-2008 Alexander Roshal


Extracting from /home/user/file1.rar

Extracting  /home/user/file1                                              40%  OK 
All OK
```

but! when I comment the "exec" line I get this:

```
unrar x -p****** /home/user/file1.rar /home/user
unrar x -p****** /home/user/file2.rar /home/user
unrar x -p****** /home/user/file3.rar /home/user
```

does anybody know what am I doing wrong? thanks and sorry if my english isn't good

---

### Post by carrett on 2009-01-28
try this

```
#!/bin/sh
PASS=`zenity --entry --title="unrar password protected files" --text="Password:" --hide-text 2>&1`
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
   echo unrar x -p"******" "$FILE" "`dirname $FILE`" >> unrarpass.log && exec unrar x -p"$PASS" "$FILE" "`dirname $FILE`" >> unrarpass.log
   done
```

Just a guess :)

---

### Post by cafeytv97 on 2009-01-28
no, it still uncompress just one file. but thanks anyway!

---

### Post by khedron on 2009-01-28
> **cafeytv97 said:**
> 
```
#!/bin/sh
PASS=`zenity --entry --title="unrar password protected files" --text="Password:" --hide-text 2>&1`
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
   echo unrar x -p"******" "$FILE" "`dirname $FILE`" >> unrarpass.log
   exec unrar x -p"$PASS" "$FILE" "`dirname $FILE`" >> unrarpass.log
   done
```

What's wrong is the use of the word **exec**.

Try this:
```
#!/bin/sh
PASS=`zenity --entry --title="unrar password protected files" --text="Password:" --hide-text 2>&1`
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
   echo unrar x -p"******" "$FILE" "`dirname $FILE`" >> unrarpass.log
   unrar x -p"$PASS" "$FILE" "`dirname $FILE`" >> unrarpass.log
   done
```The reason for this is that **exec ***replaces *bash with the new program (in this case, unrar) so when the program finishes, the whole script finishes. I.e. as soon as the first unrar completes, the script finishes.

Without exec, bash remains in the background and continues with the script after the first unrar completes.

---

### Post by cafeytv97 on 2009-01-28
yes... it works, thank you! now I can sleep

---

### Post by khedron on 2009-01-28
Good night!

BTW, put [solved] in the title of this thread if you can, so others know that your problem's solved.

---

