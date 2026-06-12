---
title: "Flex...How do I fix this message?"
date: 2008-12-28
forum: General Help
---

### Post by lightshayde on 2008-12-28
```
william@Retupmoc:~$ sudo apt-get install flex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flex is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flex has no installation candidate
william@Retupmoc:~$ 
```

I already searched for an answer to this question and went to [http://ubuntuforums.org/showthread.php?t=106156](http://ubuntuforums.org/showthread.php?t=106156), but when I typed in 'sudo apt-get install flex the above message came up.

To clarify, I want to install WINE but my Ubuntu computer isn't hooked up. I am trying to install from source.

---

### Post by adult swim on 2008-12-28
when you say your computer isnt hooked up im guessing you mean hooked up to the internet.  if this is the case you will not be able to install anything from apt-get as it uses the internet.  if you have some sort of removable drive then you can download a flex deb package here, put it on your computer, and double click the file to install it.  [http://dir.filewatcher.com/d/Ubuntu/i386/devel/flex_2.5.31-31_i386.deb.256136.html](http://dir.filewatcher.com/d/Ubuntu/i386/devel/flex_2.5.31-31_i386.deb.256136.html)

however, you might want to think about installing wine from a deb package from their website, you wont have to worry about dependencies and such. 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by bodhi.zazen on 2008-12-28
To be honest I think you are best off connecting to the internet. How did you get the source code if not from a download ?

So, why not download the wine.deb ?

You might also want to look at aptonCD

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

If you wish to install from source you will need to install build-essential and the dependencies, including the "dev" packages.

---

### Post by lightshayde on 2008-12-28
Thanks...Aptoncd looks pretty useful.

I have two computers, one running on XP and hooked up to the Internet (the one that I'm on right now) and my other one, with Ubuntu. 

I do have a flash drive; this is how I'm transferring files between the two. 

I believe that the .deb package doesn't work without an internet connection. I'm not sure though.

---

### Post by bodhi.zazen on 2008-12-28
.deb packages work just fine without an internet access, it is just you can not download / install the dependencies.

---

