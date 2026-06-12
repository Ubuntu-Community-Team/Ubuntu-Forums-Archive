---
title: "dpkg problem"
date: 2006-07-14
forum: Desktop Environments
---

### Post by goneflyin on 2006-07-14
I'm new to ubuntu and I wanted to update my system as well as install an application, but whenever I try to I keep getting this message

 dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


How do I fix it that and what does it mean. 

Thanks,
Chris

---

### Post by TheBlackNoodle on 2006-07-14
Try using Applications->Accessories->Terminal. A command prompt should pop up. Type:

> sudo dpkg --configure -a

and hit enter. "sudo" will give you superuser privileges, and allow you to run this command.

P.S. If Terminal is not in the Accessories sub-menu, try Applications->System Tools->Terminal. I can't remember which menu it's actually in.

---

### Post by rivode on 2006-07-14
dpkg is the program that is responsible for looking after packages of software on your computer.  The update program downloads new packages, then passes them to dpkg to be installed.  Normally there is no problems in doing this.

The error message you are getting is asking you to run a program from a terminal window, but it seems that doing this doesn't help.

I'm having a similar problem at the moment as well.  Also, when I run 'sudo apt-get upgrade' or 'sudo dpkg --configure -a', this gets shown:
```

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

I can't remember what I was trying to install when I first got this message.  Any ideas on how to fix this?

This probably doesn't belong in this forum, I'll re-post it in the 'repository support' forum if necessary.

---

### Post by vem0m on 2006-07-14
hmmmmm forgot how i fixed something similar seems it got cut off when installing something in the past either thu that command or anyother package manager might search the forums as i seen it here how to force it to end it or finish the old install of whatever :P

---

### Post by goneflyin on 2006-07-14
when I type that at the terminal all it does is show me some man pages but nothing about fixing the problem. 

Chris

---

### Post by goneflyin on 2006-07-14
well it seems to be working now. when I typed sudo dpkg --configure -a the first time it showed me the man pages, then I closed that and when it returned to the command prompt I typed it again, it didn't show me anything or ask anything it just brought up the command prompt again. So I tried installing an app and it worked. :)

---

### Post by vem0m on 2006-07-14
hehe yea that was the command :P

---

### Post by rivode on 2006-08-01
I managed to get my system working again by removing the package 'python-subversion'.

---

