---
title: "mounting a CD and using options"
date: 2007-11-02
forum: Desktop Environments
---

### Post by corn29 on 2007-11-02
Hello,

I have a CD with 4 files on it.  In Solaris and Windows, I see the four files.  In Fiesty, I only see 3... a file named .CD_info is missing.

I tried to mount the CD/DVD drive with # mount /media/cdrom0/ -o unhide.

It still doesn't work.  As a workaround, I had to copy the CD to a temp folder, go to Windows and transfer the .CD_info file to a USB drive.  And then I transfered the file from USB to the temp folder.  As you can imagine, this solution st!nks.  

What is a way I can see all of the files on my CD?

Thanks!

---

### Post by shad0w_walker on 2007-11-02
Any file begining with a . in Linux is counted as hidden. If your in nautilus hit Ctrl + H to show it up.

---

### Post by daengbo on 2007-11-02
You can right-click in the window and "Show hidden files"

---

### Post by john lejeune on 2007-11-02
Hello corn29,
As shad0w_walker says, any file prefixed with . is hidden.
In a terminal, you can use the -a option of the "ls" command.

Your cdrom is automounted in /media, so:
```
ls -a /media/cdrom/
``` will list ALL the documents in your directorie.
You'll always see a . and a .., respectively "the directorie itself" and "the parent directorie".
```
cd /media/cdrom
ls -al
cd ..
``` will move you to the parent dir, /media in your case.

The . is useful when you want, for example, copy (cp) something from "there" to "where I am":

```
cp /home/Desktop/something.txt .
```

---

