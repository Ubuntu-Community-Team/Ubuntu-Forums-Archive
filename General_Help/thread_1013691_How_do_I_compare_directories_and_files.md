---
title: "How do I compare directories and files?"
date: 2008-12-17
forum: General Help
---

### Post by agrozdanov on 2008-12-17
I have Ubuntu machine with one directory containing about 100000 files in subdirectories and another, similar- one, on an external hard disk- synology. I'd like to see which files are different between the two directories and to remove duplicates. Does anyone know a good way to do this? Thank you

---

### Post by vanadium on 2008-12-17
You want the two directories to be identical after the comparison?

---

### Post by eraker on 2008-12-17
```
diff -u <(ls /full/path/of_1st_directory/for/comparison) <(ls /full/path/of_1st_directory/for/comparison)
```

I got this from a great bash site: [shell-fu]("http://www.shell-fu.org/")

And I made a bash script out of it, so I could just remember the script name (with the useful command in bold): 
```

#!/bin/bash
# compare output two directories


Usage="Enter Full path for two directories for comparison, no more and no less."

if [ $# -le 1 ]
then
    echo -e $Usage
    exit 1
elif [ $# -eq 2 ]
        then
        **diff -u <(ls $1) <(ls $2)**
        exit 0
elif [ $# -gt 2 ]
then
    echo -e $Usage
    exit 1
fi
```

This won't totally solve your problem, however, because it won't auto-remove the duplicates.  

You can also add the -R flag to ls to move recursively through directories:
```
diff -u <(ls -R /directory1) <(ls -R /directory2)
```
Then, you'd have to get that to find and print the **full path of the files** without a "-" or a "+" in **only one** directory (these would be duplicates), after which you can pipe that output to "xargs -o rm -if", but I'm stuck on the middle step. 

I guess there's a couple of ways to do it, but I can't figure out the best way right now that won't do too much.

---

### Post by eraker on 2008-12-17
I got stuck on this problem, which I thought would only take a moment to figure out, and I ended up starting a thread in the programming section:
[http://ubuntuforums.org/showthread.php?p=6388018&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?p=6388018&nojs=1#goto_threadtools) to answer the question that came up for me.

You may not be interested in that academic question, but it is often possible to find really good solutions to this stuff via [google]("http://www.google.com/search?q=script+to+remove+duplicate+files&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a"). Here's a powerful and smart (but also potentially dangerous) solution, for instance:
[http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/](http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/)

This script is good because it outputs a shell-script with commented-out remove commands, so you can actually go through and see what's going to be removed before you edit the file so that these things get removed (and if you let it remove everything it would remove every instance of the duplicate file).

---

### Post by doobiest on 2008-12-17
I prefer this

diff -y -I RE <(ls -R -1 /dir1) <(ls -R -1 /dir2) |more

This will only show difference not matches. It will put them in a side by side column. |more is optional of course

---

### Post by unutbu on 2008-12-17
There is also meld -- it's a package in the official repos.

```
Description: graphical tool to diff and merge files
 Meld is a tool which allows the user to see the changes in, and merge between,
 either two files, two directories, or two files with a common ancestor.
```

If you know emacs, then M-x ediff-directories is a great alternative.

---

