---
title: "need help with wordbiz install"
date: 2006-08-19
forum: Desktop Environments
---

### Post by blackdalek on 2006-08-19
Hi,
I am new to linux and I have downloaded the WordBiz scrabble clone game from [www.isc.ro](www.isc.ro) and extracted it to my home directory on my linux machine.
but when I try to run it I see the error below - what do I need to do to get this working. I don't know what the errors mean.
```
mylinux@mylinux-desktop:~/WordBiz$ java -jar wordbiz.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at aN.<init>(Unknown Source)
   at wordbiz.<init>(Unknown Source)
   at wordbiz.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...3 more
mylinux@mylinux-desktop:~/WordBiz$
```

---

### Post by blair on 2006-12-30
It appears to be a Windows-only program and you are trying to run it under Linux. When you register for an account, the next page says:

"...Next step is to download and install Wordbiz, a Windows program..."

You can not run this natively under Linux. You must use WINE or you must create a Windows virtual machine and run it from there. Considering it is Java based, that could be quite a challenge. I'm sorry I'm unable to help you there.

---

### Post by perioeci on 2007-01-18
There is a linux version:

[http://isc.ro/linux/download.html](http://isc.ro/linux/download.html)

Having the same problem...

---

### Post by blackdalek on 2007-02-16
The solution for me was to install the latest Sun Java. That fixed all the errors.

---

### Post by videodrome on 2007-03-26
FYI the java linux version of wordbiz does *definately* work under edgy.

---

### Post by calamarain on 2007-08-08
Hiya, am also having problems with this. I've installed the latest java packages, and installed gcj, which seems to have allowed the program to install (was getting the same error messages as above)

However, I seem to have a new problem. The first screen that comes up (language selection) won't respond to anything. I can change the checkboxes, but clicking on OK has no effect (though the button depresses), nor does attempting to close the program, had to kill it manually. Can anyone assist?

---

### Post by PgR on 2007-10-24
Was there a solution to this in the end?

(Trying to solve it for a friend who's objection to Linux is it won't run this one app... If I could only get it working it'd be one less windows box in the wild)

---

### Post by blackdalek on 2007-10-25
> **calamarain said:**
> Hiya, am also having problems with this. I've installed the latest java packages, and installed gcj, which seems to have allowed the program to install (was getting the same error messages as above)

However, I seem to have a new problem. The first screen that comes up (language selection) won't respond to anything. I can change the checkboxes, but clicking on OK has no effect (though the button depresses), nor does attempting to close the program, had to kill it manually. Can anyone assist?


What is gcj? I never installed that and my Java WordBiz runs fine. I think there-in lies your problem. Remove all that gcj crap plus anything else relating to Java which doesn't include "Sun" in the description...  and instead install only the sun-java6-* things... That will probably fix it.

---

