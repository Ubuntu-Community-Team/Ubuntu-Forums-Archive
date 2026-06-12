---
title: "Command syntax"
date: 2009-01-24
forum: General Help
---

### Post by GROMS on 2009-01-24
Not sure is this is the right place to ask but:

I have a directory full of files that I want to rename. The first part of the file names are the same (Time Line*)and the sufixes are all the same (.txt). I want to change the 'Time Line' part to a single character (say A). I tried using: rename 's/Time Line/A/' *
at the command prompt, it executes but does nothing, not even an error. What am I doing wrong??

---

### Post by dagnabit dang doohickey on 2009-01-24
Consulting a command's man page for proper usage will usually reap greater rewards than divining it. ;)

```
man rename
```


Edit: My bad. I was thinking about the original rename command. Ubuntu has rename symlinked to prename. Mmmm...crow.

---

### Post by kaibob on 2009-01-24
That command should work fine. Are you in the correct directory? Is capitalization in the command the same as the files? Duplicate file names?

You could try the following as an alternative:

```
for file in *.txt ; do mv "${file}" "${file/Time Line/A}" ; done
```

As always, work with duplicate files until things are tested and resolved.

---

### Post by GROMS on 2009-01-24
> **kaibob said:**
> That command should work fine. Are you in the correct directory? Is capitalization in the command the same as the files? Duplicate file names?

You could try the following as an alternative:

```
for file in *.txt ; do mv "${file}" "${file/Time Line/A}" ; done
```

As always, work with duplicate files until things are tested and resolved.

Thank you for the response. I checked that I was in the correct directory, no duplicate files and the capitalization of the command is correct (according to the man pages) but they give it as a Pearl syntax. I don't know Pearl and don't understand the syntax used. Tried it with the -n option and it gave nothing. Your code appears to be a programming language, will this work from the command line?? Also your use of the word 'file', is it a substitute for something?

The action is being taken on files on a Kingston USB drive. I think I'm at the right place but if go to root, it doesn't show me the drive. I think this may be my problem. I can get to it through Nautilus which shows it under the 'tree' along with Home and File System. Origionally I did a cd from Home which seemed to work - now I'm not so sure - better look again.
OK tried from command prompt at user home, cd 64:~$ cd /media/KINGSTON
and did an ls which showed the files and directories on the stick - so I ws in the right place at the start.

---

### Post by kaibob on 2009-01-24
I tried your rename command on some test files, and it worked fine. So, the command is OK.

Why don't you copy some of the files from the Kingston drive to one of your home directories and try the command again. Then, if that works, you can deal with the Kingston drive. Until you get things sorted out, it's probably best to use rename with the -n (no action) option. 

I don't understand your comment concerning root, but there is no reason to mess with that. Just open a terminal window, change to the directory that contains the files, and run the rename command.

When you open a terminal and change to the Kingston drive, what does it show with the following command:

```
ls -l
```

Perhaps there is a permissions issue.

---

### Post by kaibob on 2009-01-24
> **GROMS said:**
> Thank you for the response. I checked that I was in the correct directory, no duplicate files and the capitalization of the command is correct (according to the man pages) but they give it as a Pearl syntax. ...

I was referring to capitalization of Time Line in the file names (e.g. Time Line vs. Time line).

---

### Post by GROMS on 2009-01-24
> **kaibob said:**
> I was referring to capitalization of Time Line in the file names (e.g. Time Line vs. Time line).

Got it - all works fine - Thanks for the help.

---

### Post by mb_webguy on 2009-01-24
I personally use GPRename when I need to do batch renaming of files.  It's much easier than trying to remember command and regex syntax (although it still allows you to use regular expression if you want).

Glad you got the command working, though.

---

### Post by GROMS on 2009-01-25
> **mb_webguy said:**
> I personally use GPRename when I need to do batch renaming of files.  It's much easier than trying to remember command and regex syntax (although it still allows you to use regular expression if you want).

Glad you got the command working, though.

Looked GPRename up on the web and they show ver 2.6.3.tar.bz2 dated 9/08. Synaptic shows 2.5.2 dated 9/07. Which version are you using and if it is the latest (2.6*), how do you install it (newbe)??

---

