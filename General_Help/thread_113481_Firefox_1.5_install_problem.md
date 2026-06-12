---
title: "Firefox 1.5 install problem"
date: 2006-01-06
forum: General Help
---

### Post by Tosa on 2006-01-06
I installed Firefox 1.5 per [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion). After that when I started Firefox I got a message that a Firefox window was allready running and that I should close it before opening a new one!? I've checked processes and there was not any Firefox running. After reboot I got the same message...
Any help on this ?

---

### Post by veloct on 2006-01-06
Did you create a new profile or are you using the same profile you had for 1.0.7?

---

### Post by indulis on 2006-01-07
Firefox may be complaining about there being a "lock file" that it puts in your home directory when firefox starts, and it is supposed to delete when it stops.  Of course, sometimes it doesn't, then you need to remove the lock file yourself.

This *may* fix your problem.  I am not (yet) running ubuntu so the instructions are general in nature.

1) open a terminal window and type " cd ~" (dont type the quotes), or alternatively use a file browser to go to your home directory... that's what cd ~ does(make sure you have checked the option to allow you to see hidden files).

2) "cd .firefox" (or use the filebrowser to get you there).  You should see one or more directories, repeat steps 2 onwards for each of these directories.

3) "find . -name *lock*" (or use the filebrowser to look in the directories for a lock file).

4) "rm ./my_user_name/1tm3frot.slt/lock"

Try starting firefox again.  I don't know why they dont fix this in firefox, it gets me every 3-4 months or so.

Luck!

Indulis

---

### Post by orev on 2006-01-07
I have used Automatix several times to install 1.5 and it seems to work great...

maybe try the link in my signature...?

---

### Post by Tosa on 2006-01-11
Thanks Indulis, and sorry for beeing so late.

I've reinstalled FF via Arnieboys' script, but got the same problem. After I've deleted lock file everything went smooth.

---

