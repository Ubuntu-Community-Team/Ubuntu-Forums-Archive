---
title: "Can't rename/move file"
date: 2009-03-30
forum: General Help
---

### Post by kellemes on 2009-03-30
I have a file called..
```
15 - Magus Perd?flac
```

I can't rename it let alone move it or do anything else with it actually..
Surely "?" is the issue (should be a dot), but how do I fix this?

---

### Post by Dejai on 2009-03-30
Hmm thats a strange issue.... Did you try moving / renaming it in terminal?

```

mv 15\ -\ Magus\ Perd\?flac  exampleFile

```

The above worked fine on my 8.10 box.

---

### Post by j7%&lt;RmUg on 2009-03-30
Where is the file located?

It may be that you dont have permission to do anything with the file. In that case you will have to move the file using the terminal:

open up a terminal and type the following:
```
sudo mv <path to file>
```

Hope this helps.

---

### Post by kdev on 2009-03-30
Try typing "15" then hit **tab** on your keyboard, it will automatically continue the file name.

sudo mv 15**tab** newname

---

### Post by 3rdalbum on 2009-03-30
Is it a question mark inside a black diamond?

That's the symbol for when a particular special character can't be displayed using the current font. Rest assured, if you can see it in "ls", you can copy it from the output of ls and paste it into your command-line, and that question-mark character will be subsituted for the real special character.

---

### Post by kellemes on 2009-03-30
```
ls -al
ls: 15 - Magus Perd?flac: No such file or directory
total 40268
drwxrwxrwx  2 500 users        0 2009-03-30 13:03 .
drwxrwxrwx 27 500 root         0 2009-03-26 01:31 ..
-rwxrwxrwx  1 500 users 13527249 2009-02-07 06:09 02 - Prelude.flac
-rwxrwxrwx  1 500 users 27650608 2009-02-07 06:09 15 - Magus Perd?flac
```

2 files, same permissions..
I can mv "Prelude.flac" without issues.

```
sudo mv 15\ -\ Magus\ Perd\?flac testname
cannot stat `15 - Magus Perd?flac': No such file or directory
```

Graphical filemanagers do show me the filename (like ls) but permits no "mv", some filemanager (like TuxCommander) actually hang or crash when trying.

Don't get it.

Edit: VLC's openfile-dialog isn't even showing the file.

---

### Post by topdownjimmy on 2009-05-17
I'm getting this same problem.  It has to do with non-Latin characters, like é, in kellemes' case.

For me it involves files on an NTFS drive, which might be part of the problem.

I'm not the owner of these files (the owner is "35000" :confused: ), and [FONT="Courier New"]sudo mv[/FONT] doesn't work.  I still get:

[FONT="Courier New"]mv: cannot stat `filen?ame.ext' for reading: No such file or directory[/FONT]

The question mark is not in a black diamond, it's just a question mark.  I can see it with [FONT="Courier New"]ls[/FONT], with Nautilus, and with KDirStat.

There are only so many files like this, so one way to work around it is to execute [FONT="Courier New"]mv[/FONT] commands that don't include the question marks, but still reference the file in question.

For instance, in my case, I did:

[FONT="Courier New"]sudo mv filen*.* filename.ext[/FONT]

This rids the filename of those pesky question marks, and allows a [FONT="Courier New"]mv[/FONT] to be performed on the file.

Might be a bit tedious if you have lots to work with, but this is one way of doing it.

Anybody have any better solutions?  Is there a way to rename a group of files with just the first three letters in their filename, and their current extension?

---

