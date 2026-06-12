---
title: "Black screen &amp; flashing cursoe?"
date: 2010-01-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by altjx on 2010-01-25
All I did was wake up this morning and turn the computer on, and now it doesn't go anywhere. It sits at a flashing cursor. 
 
I have a dell inspiron 1545. it was working fine yesterday. I'm pretty new to linux, switching from windows, but its always some problem. I just DL'd and installed it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) so I'm not 100% on the version and everything. i DL'd this 2 days ago
 
Also, it's not my hard drive going bad, I'm 100% on that. I'm not dual booting or anything, just straight Linux and run into this problem. I've been googling and searching the forum for awhile, but no one seems to be having the exact same problem
 
Weird, now it's working. All I did was boot from the CD and try fixing broken packages, updating, and rebooted. They all failed but it worked for some reason. Anyone know how to prevent this in the future?

---

### Post by coffeeaddict22 on 2010-01-26
Hi alt,
Welcome to Ubuntu!
You're describing a terminal: a black screen and a flashing cursor.  Normally the system boots up through the GRUB menu into a graphical user interface (or GUI).  The terminal has its uses, and for some uses it's essential, so it still maintains a big presence in Linux.  Anytime you want to see one, hit [Ctrl- Alt] + any of F1 to F6; Ctrl- Alt -F7 will bring up the GUI again.

Because its so useful, there's a few ways you could have got into it.  The GRUB menu where you choose which operating system you're going to use has a terminal option- that's the recovery version of your current OS.  The shortcut keys above could have done it.  There's a selection at the login screen  from memory as well.  Try googling terminal, or CLI (command line interface).  

If the system can't boot up OK, it'll often drop you into a CLI so you can fix the problem, or at least figure out where the problem was.  For instance, there's a series of log files ( have a look in System/Administration/Log file viewer, or (in a terminal ) the files in /var/log) that you can skim through to try to identify why the system spat the dummy

All up, don't know how you got there, but you got out OK.

---

### Post by altjx on 2010-01-29
blah, i still get the issue every now and then, its weird as hell

---

