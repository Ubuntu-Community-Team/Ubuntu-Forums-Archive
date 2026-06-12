---
title: "nautilus will not open folder"
date: 2008-02-07
forum: Desktop Environments
---

### Post by rplantz on 2008-02-07
I have one folder in my home directory that nautilus will not display the contents. When I double-click on the folder (or use nautilus /home/bob/my_folder) it brings up a window and shows the correct number of items in the folder. But the items are not shown, and after a few seconds the window goes dim.

I can log into my xfce desktop and thunar opens the folder just fine.

What do I need to tweak in order to get nautilus to work with this folder properly? It works just fine with at least a couple of dozen other folders.

---

### Post by bwhite82 on 2008-02-07
Are they hidden items? In Nautilus goto View>Show Hidden Files to view them if they are. (Not trying to insult you, I always start with the simple items when giving advice). Can you view the output of the folder with the CLI command?:

> ls -a

---

### Post by rplantz on 2008-02-07
> **Soldierboy said:**
> Are they hidden items? In Nautilus goto View>Show Hidden Files to view them if they are. (Not trying to insult you, I always start with the simple items when giving advice). Can you view the output of the folder with the CLI command?:

No, they're not hidden. For example,
```

bob@ubuntu:~/my_book_hrdwr$ ls -a
.                      10_locals.aux              allan_io              book_cover.tex        cpu_decoder.ps       lstlang0.sty
..                     10_locals.tex              AN-55.pdf             book.dvi              d_embed.aux          lynn_feedback
00_letter.tex          11_write_func.aux          an9722.pdf            book_figs             d_embed.tex          make_example
00_preface.aux         11_write_func.tex          an9836.pdf            book.idx              dn285f.pdf           Makefile
-----------

```
(I added the "-----------" to avoid showing everything here; there are over 100 items in the directory.)

When I try to open the folder in nautilus, it (nautilus) simply hangs. If I have other nautilus windows open, they become unresponsive. My CPU starts running at full speed with nautilus taking about 80% of the time. I have to force nautilus to quit.


Thank you for your tactful remarks. I'm not at all insulted. I've made MUCH more stupid mistakes in my life. :)

---

### Post by rplantz on 2008-02-07
Okay, I solved the problem. There was something wrong with one file in the folder. I used a "brute force" technique to find the offending file. First, I created a new folder. Then I used the command line in a terminal to copy groups of files over. For example,
```

cp -a *.tex ../temp/

```
copied all my LaTeX source files.

After each copy, I would check to make sure that I could still open the new folder in nautilus.

It turned out to be the last file I copied! No, I'm not kidding here. It was a plain ol' text file. Simply using the command line to make a copy of it, then deleting the original worked. I'm pretty sure that something in the file system structure of the offending file got screwed up. Sigh.

Edit: Of course, that still leaves the question of why thunar would open the folder but nautilus would not.

---

### Post by bwhite82 on 2008-02-07
Hm...that certainly is a head-scratcher. :-k Glad you got it all worked out though.

---

### Post by ejket on 2008-02-08
> **rplantz said:**
> After each copy, I would check to make sure that I could still open the new folder in nautilus.

It turned out to be the last file I copied! No, I'm not kidding here. It was a plain ol' text file. Simply using the command line to make a copy of it, then deleting the original worked. I'm pretty sure that something in the file system structure of the offending file got screwed up. Sigh.

Edit: Of course, that still leaves the question of why thunar would open the folder but nautilus would not.

It was the filename or else the directory entry got corrupted somehow.  Do you remember exactly what the filename was?  No special characters, especially the first character?

The two file managers would have different error trapping code, so it's not such a surprise that you'd get different outcomes.

---

### Post by rplantz on 2008-02-08
> **ejket said:**
> It was the filename or else the directory entry got corrupted somehow.  Do you remember exactly what the filename was?  No special characters, especially the first character?

The file was named "allan_io", which is not very weird. Of course, I could have hit the wrong key or something when renaming it. But I don't recall renaming it, and I had been doing lots of work in that directory up until a couple of months ago.
> 
The two file managers would have different error trapping code, so it's not such a surprise that you'd get different outcomes.
Yes, I hadn't thought of that. My first thought was "magic." :)

---

