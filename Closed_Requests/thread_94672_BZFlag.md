---
title: "BZFlag"
date: 2005-11-24
forum: Closed Requests
---

### Post by Tyaedalis on 2005-11-24
Can someone compile bzflag?

i dont seem to have the 'make' command on my computer...

---

### Post by noigeaR on 2005-11-24
on a terminal type
```
sudo apt-get update
sudo apt-get install build-essential

```
this installs make, gcc, etc.
you could also use synaptic or adept (on kubuntu) to install this package.
you might have to install other packages to install bzflag, but at least build-essential installs all the basics for compiling programs yourself.

---

### Post by akurashy on 2005-11-24
it already been requested, I don't know if they are in the backports yet

---

### Post by benplaut on 2005-11-24
the binaries on the bzflag site work just fine... no need to compile

---

### Post by jdong on 2005-11-24
jdong@shuttle:~$ ubp bzflag
    bzflag | 2.0.4.20051017 |      unstable | source, i386
    bzflag | 2.0.2.20050318ubuntu2 |        breezy | source, i386
**    bzflag | 2.0.4.20051017ubuntu1~breezy1 | breezy-backports | source, i386**
    bzflag | 2.0.4.20051017ubuntu1 |        dapper | source, i386

The latest version is already in breezy-backports.

---

### Post by Tyaedalis on 2005-11-25
where can i find this?

---

### Post by noigeaR on 2005-11-26
Ubuntu Forums - Getting Started With Backports
[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

---

### Post by mkeidel on 2005-11-28
I added the Breazy backports and bzflag upgraded to version 2!  Works great except:
  only bottom left quadrant shows the action - the other three quadrants only show some sort of texture...   not usable.. bummEr!:???:

---

