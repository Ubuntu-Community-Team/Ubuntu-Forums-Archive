---
title: "Request: Lyx v1.4.1 package"
date: 2006-07-05
forum: Desktop Environments
---

### Post by eitan on 2006-07-05
hello,

  i'd like to request v.1.4.1 of the package "lyx" in the repositories.
  the current version in the repository is 1.3.7.

thank you,
/ eitan

---

### Post by kleeman on 2006-07-15
I asked for a backport from edgy (which has 1.4.1) but there are (silly) dependency issues. Pick up some custom dapper debs here:

[http://www.math.nyu.edu/faculty/kleeman/lyxdapper.tar](http://www.math.nyu.edu/faculty/kleeman/lyxdapper.tar)

untar them with:

tar xvf lyxdapper.tar

and they are in a debs subdirectory.

---

### Post by hogweed on 2006-07-15
I just saw that 1.4.2 is out now. Anyone have dapper debs for that one? I have been compiling a single binary and using that, but would like to stop if  possible...

-- hogweed

---

### Post by kleeman on 2006-07-15
It should be in Debian unstable fairly soon. When it is I'll try a deb compile. Seems worthile as there are many bugfixes.

---

### Post by hogweed on 2006-08-04
Any luck on 1.4.2? I have seen that it is in both Edgy and Deb unstable now...

---

### Post by kleeman on 2006-08-05
Tried it and it doesn't want to build. Seems like it needs an updated (edgy) dpkg. I have a checkinstall deb if you are interested:

[http://www.yourfilelink.com/get.php?fid=149145](http://www.yourfilelink.com/get.php?fid=149145)

You need to remove the old lyx packages (all of them).

---

### Post by hogweed on 2006-08-07
This will do for now. Thanks!

---

### Post by kmkz on 2006-09-17
I'm using Dapper Drake 6.06 Release and I was wondering if it is possible to upgrade to Lyx 1.4.2 (I got version 1.3.7).
How do I do it ? 
thanks.
(sorry if this is a simple question, but I'm new to linux)

---

### Post by kleeman on 2006-09-17
Start up synaptic (System---->Administration----->Synaptic Package Manager)
Search for "lyx".
Mark all installed lyx packages (you might have three installed) for removal.
Remove.
Click on my link above in this thread and then click on download file.
A dialog box comes up asking if you want to open with gdebi or download.
Open with gdebi
Install package.
Launch lyx from a console with /usr/local/bin/lyx

---

### Post by kmkz on 2006-09-17
thanks kleeman.
I downloaded you file, unpacked it and run gdebi. However, when I run it on the lyx_1.4.1-1.lyx.org.1_all.deb file, it automatically downloads all the other 3 packages directly from Ubuntu's repository (version 1.3.7). If I try to install lyx-common first, I got an error " conflicts w/ the intalled package lyx-qt" - however, I did remove all lyx packages as you said. I'll try to restart the computer and do it all over to see if it works.

I've checked the "mark for complete removal" box in th Synaptic Package Manager, but when I try to install lyx-common it says it conflicts with lyx-qt. If I try to install lyx-qt it says it depends on lyx-common and stops.

---

### Post by kleeman on 2006-09-17
I think you downloaded the wrong file. Look at my August 5 post above, it has lyx-1.4.2 not 1.4.1.

---

### Post by kmkz on 2006-09-17
Oops!
It worked now.
thanks again!

---

