---
title: "libtrash not moving rm files to Trash"
date: 2009-03-01
forum: General Help
---

### Post by huffy318 on 2009-03-01
When i rm a file, it doesn't get moved to trash.

While playing around, i made a .libtrash file with this:
INTERCEPT_OPEN = YES

Now if i open a file in emacs, and change it, the old file does in fact get copied into Trash.

But changes to the file (rm or commands like echo "dsadsdsafdsa" >> tr.txt) from the terminal (i happeded to try xterm, rxvt & gnome-terminal) do not.

Is there something i can change to get libtrash to intercept commands from the terminal?

I am using Intrepid 8.10

---

### Post by phenest on 2009-03-07
I would also like to know how to make it work.

I think libtrash should be installed and setup by default.

---

### Post by dcstar on 2009-03-07
> **huffy318 said:**
> When i rm a file, it doesn't get moved to trash.
........

Trash is something that a Desktop GUI environment provides, command line rm is not a GUI tool so it knows nothing about such things.

If you want the "rm" command to use the GUI trash, then you will have to create a "rm" script to replace the original command (plenty of examples in Google).

---

### Post by huffy318 on 2009-03-08
> **dcstar said:**
> Trash is something that a Desktop GUI environment provides, command line rm is not a GUI tool so it knows nothing about such things.

One purpose of libtrash is to provide Trash for the command line, including rm:

[https://launchpad.net/ubuntu/intrepid/ia64/libtrash]("https://launchpad.net/ubuntu/intrepid/ia64/libtrash")

---

### Post by gasull on 2010-03-24
Same problem over here.

A workaround I'm using is:

```
alias rm="gvfs-trash"
```

Of course it isn't the same since I want to have deleted files moved to the Trash folder for every application, not just the command line.

---

### Post by Seq on 2010-03-24
You've logged out after setting it up, right? As a library, it needs to be loaded before your shell/session is.

---

### Post by gasull on 2010-03-24
> **Seq said:**
> You've logged out after setting it up, right? As a library, it needs to be loaded before your shell/session is.

I think I'm doing it right.  Can you please tell me what's wrong with these commands?

```
gasull@sanfran:~/Desktop$ export LD_PRELOAD=/usr/lib/libtrash/libtrash.so.2.4 
gasull@sanfran:~/Desktop$ bash
gasull@sanfran:~/Desktop$ cat > foofadsfasdfa
fdslajfaldf
gasull@sanfran:~/Desktop$ rm foofadsfasdfa 
gasull@sanfran:~/Desktop$ ls ../Trash
gasull@sanfran:~/Desktop$ 

```

---

### Post by Seq on 2010-03-24
> **gasull said:**
> I think I'm doing it right.  Can you please tell me what's wrong with these commands?

```
gasull@sanfran:~/Desktop$ export LD_PRELOAD=/usr/lib/libtrash/libtrash.so.2.4 
gasull@sanfran:~/Desktop$ bash
gasull@sanfran:~/Desktop$ cat > foofadsfasdfa
fdslajfaldf
gasull@sanfran:~/Desktop$ rm foofadsfasdfa 
gasull@sanfran:~/Desktop$ ls ../Trash
gasull@sanfran:~/Desktop$ 

```

That should probably have work. No idea then, sorry.

---

### Post by gasull on 2010-03-27
I found the solution.  The libtrash version included in Ubuntu is quite old.  It has been the 2.4.2 since Intrepid.  There is an unofficial repo with libtrash 3.2 at [https://launchpad.net/~softec/+archive/ppa](https://launchpad.net/~softec/+archive/ppa)

It's working for me now.

Cheers.

---

### Post by huffy318 on 2010-03-29
Does it work for all applications for you now?

---

### Post by gasull on 2010-03-29
> **huffy318 said:**
> Does it work for all applications for you now?

I use it just for Midnight Commander.  And yes, it works.

---

### Post by laramichaels1978 on 2010-03-29
> **huffy318 said:**
> 
Now if i open a file in emacs, and change it, the old file does in fact get copied into Trash.

But changes to the file (rm or commands like echo "dsadsdsafdsa" >> tr.txt) from the terminal (i happeded to try xterm, rxvt & gnome-terminal) do not.


Works just fine here. :) I think libtrash ignores empty files (explained in the readme.txt IIRC).  don't know about shell redirection, though

~l

---

### Post by Boetius on 2013-02-04
Libtrash worked in my ubuntu 12.04 (pecise) only when I installed the new version from the source according to the advise in

[http://distrowatch.com/weekly.php?issue=20120806&mode=68#qa]("http://distrowatch.com/weekly.php?issue=20120806&mode=68#qa")

However, to get it work in Gnome Commander, I had to make a launching script like this:

#!/bin/bash
export LD_PRELOAD=/usr/local/lib/libtrash.so
gnome-commander

---

### Post by oldos2er on 2013-02-04
Old thread closed.

---

