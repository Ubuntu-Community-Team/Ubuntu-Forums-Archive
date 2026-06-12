---
title: "How to delete all the hidden files in a partition?"
date: 2009-01-12
forum: General Help
---

### Post by Quaxo76 on 2009-01-12
I have a huge collection of mp3 files (about 40000 files, stored in thousands of folders/subfolders). I keep my music organized with rhythmbox. The music library is not physically located on my pc, but on a remote file server.
When I edit file tags from within rhythmbox, the operation sometimes fails; when this happens, an hidden file is left on the library's hard disk.
If for example I was editing the tags of the file /myfolder/mysong.mp3 and the operation fails, the original file stays unchanged, but there'll be a new file called /myfolder/.mysong.mp3XXXXX where XXXXX is a random number/code. That hidden file is corrupted (and of course invisible), and takes up valuable space. So I would like a command to delete all the hidden files in a given folder and its subfolders, possibly asking for confirmation before each file. I tried something like ```
rm -r -i .*.mp3*
``` but that doesn't work. Even if I type ```
ls -R .*.mp3*
``` it only lists any matching file *in that folder*, without digging into subfolders. Why? How can I do?

TIA
Cristian

---

### Post by cb34 on 2009-01-12
that's real weird.. i just tried 'ls -R .*' from my home dir to try and help you out, and it lists everything recursively just fine.

try to maybe use the 'locate' command..

try to run 'ls -R .*' from your home dir and see if it starts listing everything recursively, if not, then there's some problem.

edit-> when i run your exact command you're trying, and i do have mp3's in there.. it is also only checking the current dir.. so there is something wrong with the formating of your ls query.. even though it looks right to me as well. ????? there must be some flag that we're both missing, try lookin deep in 'man ls' may be something in there about it. sorry i cant really help you.. dont know.

---

### Post by vanadium on 2009-01-12
ls -R will only work as you expect when you give directories as argument. It will then recurse into the directories given.

For what you want to do, you can use find

```

find . -name '.*.mp3*'

```

With the -exec option, you can delete all files found right away

```

find . -name '.*.mp3*' -exec rm "{}" \;

```

Be careful with that command!

---

### Post by dagnabit dang doohickey on 2009-01-12
You may want to prefix the pattern with \. else you run the risk of another ubuntuforums post titled "Hey, where did my mp3 files go?"

---

### Post by cb34 on 2009-01-12
something i just found about ls, may help you understand what's goin on..
[http://www.linuxquestions.org/questions/linux-newbie-8/recursive-ls-642091/](http://www.linuxquestions.org/questions/linux-newbie-8/recursive-ls-642091/)

and this thread about rm
[http://ubuntuforums.org/showthread.php?t=419140](http://ubuntuforums.org/showthread.php?t=419140)

hope something in here helps you. :)

peace.

---

### Post by Quaxo76 on 2009-01-12
Whoa, lots of info... thank you! Vanadium's commands seem like the way to go in my case (but I'll add the -i option to rm, because otherwise it would delete any mp3 file starting with a '.' - even if it's not a hidden file).

Actually, I just found that the command to find only the files I want to delete is: ```
find . -name '.*.mp3?*'
``` (note the question mark after 'mp3').

By the way, what's the meaning of ```
 "{}" \; 
``` ?

Thank you again!

---

