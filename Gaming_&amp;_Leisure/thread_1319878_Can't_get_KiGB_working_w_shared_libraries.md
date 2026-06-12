---
title: "Can't get KiGB working w/ shared libraries"
date: 2009-11-08
forum: Gaming &amp; Leisure
---

### Post by DarkGob on 2009-11-08
Trying to run the KiGB emulator ([http://kigb.emuunlim.com/](http://kigb.emuunlim.com/)) and I get the following error:

```
./kigb: error while loading shared libraries: NL.so.1.6: cannot open shared object file: No such file or directory

```

According to the readme:
>     Starting from v1.11, KiGB is linked statically except the HawkNL library.
    To set up HawkNL library, copy the file libNL.so.1.6.4 to /usr/local/lib.
    Then, change directory to /usr/local/lib. Add a soft link: ln -s
    libNL.so.1.6.4 NL.so.1.6. You have to be root to do this.

I've tried this.  Didn't work.  I've tried doing this in /usr/lib instead (found another version of the Readme that said this would be necessary for Debian).  Also didn't work.  Are these instructions not accurate for Ubuntu, or am I missing something?

---

### Post by Perfect Storm on 2009-11-09
Make sure you launch the binary while you're in the same directory.

```
sh -c "cd <path> && ./kigb"
```

Otherwise if it didn't help. Double check if you made the symblink correct.

---

### Post by DarkGob on 2009-11-09
I get the same error if I try running it from the same directory.

This is the link I created, according to ls -l:

lrwxrwxrwx 1 root root 14 2009-11-07 00:30 NL.so.1.6 -> libNL.so.1.6.4

---

### Post by Perfect Storm on 2009-11-09
Try check the binary with ldd command.

ldd <binary file>

It might tell you where it are looking for the lib.

---

### Post by DarkGob on 2009-11-09
That did the trick, it turns out it was looking in /usr/lib32.  Thanks a bunch for your help.

---

### Post by Perfect Storm on 2009-11-09
My pleasure ^_^

You can add <SOLVED> to your thread by "Thread Tool".



regards
A.I. Dude

---

