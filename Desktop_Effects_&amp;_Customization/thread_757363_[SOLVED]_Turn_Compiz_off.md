---
title: "[SOLVED] Turn Compiz off"
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by actioncomics on 2008-04-16
On my son's computer he was playing around with the window transparency and has made everything transparent.  I am still some what new to linux and have not used the command line as much as I should be.  If someone would not mind to answer a couple of questions:

1.  how can I get out of the X-server to a command line?
2.  what is the command to shut down compiz?
3.  And how do I get back into the X-server (without restarting computer) to run my package manager or fix problem?

or
using a live cd what configuration files could I delete to reset compiz?

everytime I do a search on turning off compiz i come up with the "compiz-fusion icon".  this is not what i need since we can not see anything, every window is completely transparent.

Trust me this will not happen again since as soon as we get this problem fixed I will put an extra user on there so someone else can login and fix the problem.  thanks for any help.

ac

---

### Post by mrmiserable on 2008-04-16
press Alt + F2 and type 

metacity --replace

that should do it you may need to type blind

---

### Post by ad_267 on 2008-04-16
Hit Ctrl-Alt-F1 to get to a command line and log in. Ususally you could run "metacity --replace" to use metacity instead of compiz but that won't work from a separate session. It might be easiest to delete your current compiz configuration file. I think this is in ~/.config/compiz

Edit: Do what mrmiserable said, that will probably be easiest.

---

### Post by steveneddy on 2008-04-16
To turn off Compiz, go to

System --> Preferences --> Appearance

the tab at the top right labeled "Visual Effects"

click it

select "none"

You are done.

---

### Post by actioncomics on 2008-04-16
tried metacity --replace.  did not work.
tried removing config file located in /home/user/.config/compiz using the rm command.  did not work.  but I booted a live cd.  logged in as root and started deleting random files :lolflag:.  ok so they were not so random.  the file i deleted was /etc/compizconfig/config.  rebooted the machine and everything seems to work.

one last question.  how do i mark this as solved?

---

### Post by overdrank on 2008-04-16
> **actioncomics said:**
> tried metacity --replace.  did not work.
tried removing config file located in /home/user/.config/compiz using the rm command.  did not work.  but I booted a live cd.  logged in as root and started deleting random files :lolflag:.  ok so they were not so random.  the file i deleted was /etc/compizconfig/config.  rebooted the machine and everything seems to work.

one last question.  how do i mark this as solved?

HI and you can mark it solved under the thread tools
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by actioncomics on 2008-04-16
thanks for the help

---

