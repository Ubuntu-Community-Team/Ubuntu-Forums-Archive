---
title: "PCGen Frustrations!!"
date: 2008-12-16
forum: Gaming &amp; Leisure
---

### Post by klaxor on 2008-12-16
Okay, I know that there have been several threads about PCGen and how to make it properly run in Ubuntu, but I have not been able to fix it!  I have none of the source materials available, even after following the EXACT same steps another user successfully used!

I need help!

---

### Post by klaxor on 2008-12-22
Figured out a crap way to do it.  Thanks for no help at all guys.

---

### Post by phasegen on 2009-03-16
I'm with you.  I'm having the same problem.  Don't give up, we can beat this.  So far I have installed pcgen 5.14 into: 

/home/phasegen/.pcgen5141/

and I've made pcgen.sh executable

When I start the program, everything looks good except there are no sources.

I think it could it be the use of underscores in the directory and file names.

I may try to do a rewrite of all the config files and see.  If it works, I'll let you know.

---

### Post by phasegen on 2009-03-16
Got it...  It's a java issue...

Try opening a shell and running:

sudo apt-get install sun-java6-jre

(This will install sun java if you didn't already install it)

then run:

sudo update-alternatives --config java
and choose /usr/lib/jvm/java-6-sun/jre/bin/java from the list

PCGen works!

---

### Post by foxfirefizz on 2010-07-10
I've tried what you're suggesting, and it didn't work. When I ran apt-get, it gave the message of "Package sun-java6-jre is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source". I have no idea what I'm supposed to do, but I would very much like to have PC Gen up and running. Any ideas that might help?

---

