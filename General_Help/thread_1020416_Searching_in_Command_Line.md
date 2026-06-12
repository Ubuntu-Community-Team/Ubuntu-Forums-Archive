---
title: "Searching in Command Line"
date: 2008-12-24
forum: General Help
---

### Post by fat_man_dan on 2008-12-24
I am attempting to find a file on my university server using the command line (as I only have ssh access). I would normally use the tree command but this is not installed. I am attempting to do it with built in linux commands. I have tried it with ls but this does not show full context of the file, and hence I still can not find it, I just now know what the full filename is.

What I would normally use:
```
tree -if | grep -i SEARCHWORD
```

What I have tried:
```
ls -R | grep -i SEARCHWORD
```

Another related question, how would I search for a word in serveral text files in multiple directories?

---

### Post by pedro_orange on 2008-12-24
Hi, merry christmas!

I'd use the find command in your situation. 
For a full listing for it's usage see this man page.

```
man find
```

If you're searching for something within a file and you want to check everything below it, I would do something like:

```
find / -type f -exec grep -H "Searchword" {} \;
```

Here you're saying, check all normal files from / down, and for each file run a grep checking for "Searchword" and give me it's filename(-H) 

Hope this helps.

---

### Post by fat_man_dan on 2008-12-24
Thank you so much for your reply, that command works perfectly on my laptop.
When I run it on my University's server I get following looping for every file that it attempt to execute the grep command on.
```
grep: illegal option -- H
Usage: grep -hblcnsviw pattern file . . .
```

Any ideas?

---

### Post by iponeverything on 2008-12-24
I use this quite a bit.

```
find | grep -i <word>

```

Between find and the pipe put the starting directory.

---

### Post by pedro_orange on 2008-12-24
Hmmm...The -H flag simply says give me the filename when you match something.

Perhaps if you shared your command with us, we can critique it. 

I suspect it's simply a case of having ordered the command incorrectly, or using flags incorrectly. 

(I don't know if I can reply unless you post rly fast cause I'm leaving work soon. woo!)

---

### Post by snova on 2008-12-24
```
find place/to/search/in -iname '*SearchTerm*'
```

---

### Post by zvacet on 2008-12-24
```
sudo find / -name package_name
```

---

### Post by dcstar on 2008-12-24
> **fat_man_dan said:**
> Thank you so much for your reply, that command works perfectly on my laptop.
When I run it on my University's server I get following looping for every file that it attempt to execute the grep command on.
```
grep: illegal option -- H
Usage: grep -hblcnsviw pattern file . . .
```

Any ideas?

All *nixs are not identical, what works on Ubuntu grep does not necessarily work on other Unix/Linux systems. Do not assume that all commands or options will behave in the same way.

---

