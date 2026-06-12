---
title: "Delete all .txt files in subdirectories"
date: 2009-03-20
forum: General Help
---

### Post by omaralqady on 2009-03-20
I want to delete all .txt files in a directory and all it's sub-directories, how can I do this using the terminal?

---

### Post by LoneWolfJack on 2009-03-20
```
find /folder -type f -name "*.txt" -delete
```

---

### Post by omaralqady on 2009-03-20
It says ```
find: `f': No such file or directory

```, am I supposed to type the folder path again after -type or what?

---

### Post by 3Miro on 2009-03-20
I think rm -fr *.txt (maybe specify a starting folder) should run, but be VERY careful. RM is a mean command and may delete important stuff. Test it first, i.e. make a folder with couple of sub-folders and then put some generic .txt and non txt files in it. See what gets deleted and what doesn't.

---

### Post by lloyd_b on 2009-03-20
> **3Miro said:**
> I think rm -fr *.txt (maybe specify a starting folder) should run, but be VERY careful. RM is a mean command and may delete important stuff. Test it first, i.e. make a folder with couple of sub-folders and then put some generic .txt and non txt files in it. See what gets deleted and what doesn't.
That will delete any .txt files in the current directories, but it will only recurse into directories whose names match "*.txt".  Shell expansion only affects the *current* directory...

Lloyd B.

---

### Post by omaralqady on 2009-03-20
Then what should I do to delete all *.txt in all subdirectories??

---

### Post by unutbu on 2009-03-20
LoneWolfJack's command should have worked. Can you show us the command you used which generated the error?

---

### Post by omaralqady on 2009-03-20
I used lonewolf's command and it generated the error in my post about the 'f' after -type in the command, that's why I asked what the 'f' refers to .

---

### Post by unutbu on 2009-03-20
"-type f" tells find to look for files, not directories.
Thus, if you have a directory named "dir.txt", it will not get deleted. 

The more likely cause of the problem is that the find command can not find the directory you specified. Does the directory path have a space in it? In that case you need to put double quotes ("...")  around the path name.

---

### Post by omaralqady on 2009-03-20
The quotes did the trick :D Thank you all very much for your help :D

---

