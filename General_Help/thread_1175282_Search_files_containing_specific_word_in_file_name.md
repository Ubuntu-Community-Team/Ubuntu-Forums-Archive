---
title: "Search files containing specific word in file name"
date: 2009-06-01
forum: General Help
---

### Post by UranUtan on 2009-06-01
Hi,

I know that studying the man pages of FIND would solve my question. I am too intimidated by its complexity for such a simple task. Hope you can have the magic syntax handy.

Example: search in /home/username/Documents all files/folders where the file/folder name contains the word 'board'

- case INsensitive
- search in all subfolders
- display results on screen
- search must be accurate (not relying on a DB that is update from time to time. Like locate?)

Thanks in advance for any help.

---

### Post by kaibob on 2009-06-01
The following will do what you want:

```
find /home/username/Documents -iname "*board*"
```

You can add the option, -type f, to limit the search to files and -type d to limit the search to directories. The option -iname makes the search case insensitive; change this to -name if you want the search to be case sensitive.

---

### Post by andrew.46 on 2009-06-02
Hi UranUtan,

> **UranUtan said:**
> I know that studying the man pages of FIND would solve my question. I am too intimidated by its complexity for such a simple task. Hope you can have the magic syntax handy.

I see that kaibob has already helped you out with the syntax but this is probably as good a time as any to pimp a guide I have written that hopefully takes some of the pain out of 'find':

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

Once you have been through this try printing off the man page and with any luck it will make more sense?

Andrew

---

