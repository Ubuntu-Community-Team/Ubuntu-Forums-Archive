---
title: "Having severe issues after a crash..."
date: 2008-06-10
forum: Desktop Environments
---

### Post by Gilrad on 2008-06-10
Hello, I'm using Ubuntu Hardy on an Asus EEEpc 700. After a crash (I had to manually force the power off after the thing didn't shut down after around 10 minutes of waiting), whenever I login, I am bombarded with tons of error messages and am presented with a mostly broken desktop. I have had this issue before, usually solved by running the recovery console and going down the list of options, but this time it doesn't help.

The error messages are something like this (maybe with typos because I'm typing it all by hand):

GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://gnome.org/projects/gconf/](http://gnome.org/projects/gconf/) for information. (Details - 1; IOR file '/tmp/gconfd-gilrad/lock/ior' not opened successfully/ no gconfd located: input/putput error 2: IOR file '/tmp/gconfd-gilrad/lock/ior not opened successfully, no gocnfd located: input/output error)



Now I'm not a very adept linux user at all--I can't even figure out how to open the terminal when there's no menu available--so any help you can offer in the easiest terms possible would be appreciated.

Thanks!

---

### Post by Doodlemepink on 2008-08-14
Im having the same problem, and am about as skilled as you are. Help!

---

### Post by Kevbert on 2008-08-14
You could try pressing Alt+F2, then type in xterm in the box that appears and press return to get terminal to appear.
If you can get wireless or ethernet to connect you could try using
```
sudo apt-get install -f
```
in xterm to try to repair some of the broken packages.

---

### Post by Doodlemepink on 2008-08-14
ok so i figured it out. start up your machine, and after your done getting the error messages go to your hard drive,open up etc, then there will be a folder "gconifg- something", and it should show nothing in that file. Delete it. now as a caveat you *may* loose your settings like your background and such. but that is about it. restart or log out and every thing should work like a charm. it worked for me I hope it does the same for you.

:)

---

