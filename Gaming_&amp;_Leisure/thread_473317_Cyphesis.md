---
title: "Cyphesis"
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-06-13
Anybody have any idea about this: [http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/MUD/Cyphesis-3002.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/MUD/Cyphesis-3002.shtml)

And have any idea how to make it run? I changed the permission of the file, ran it, and then tried "cyphesis" from a terminal and got this:

@DualCore-Feisty:~$ cyphesis
2007-06-13 22:01:44 ERROR Unable to open event log file "/usr/var/tmp/cyphesis_event.log"
2007-06-13 22:01:44 ERROR Permission denied
2007-06-13 22:01:44 SCRIPT_ERROR /usr/lib/python2.4/whrandom.py:38: DeprecationWarning: the whrandom module is deprecated; please use the random module
2007-06-13 22:01:44 SCRIPT_ERROR   DeprecationWarning)
2007-06-13 22:01:44 ERROR Could not create local listen socket with address "/usr/var/tmp/cyphesis.sock".
2007-06-13 22:01:45 INFO Running

Any ideas? I went to the website and they call it a project called "WorldForge"

---

### Post by mediax on 2007-06-14
> **ripfox said:**
> 
2007-06-13 22:01:44 ERROR Unable to open event log file "/usr/var/tmp/cyphesis_event.log"
2007-06-13 22:01:44 ERROR Permission denied
.
.
2007-06-13 22:01:44 ERROR Could not create local listen socket with address "/usr/var/tmp/cyphesis.sock".


Those messages look like you don't have the necessary read/write for the /usr/var/tmp directory - or rather, the game doesn't.  If that's the case, then you should be able to fix it by running a CHMOD command (sorry, I don't know the correct syntax off the top of my head, but you should be able to find it either via the manual page or by searching these forums).

The SCRIPT_ERROR messages look like warnings, rather than fatal errors, so I should imagine they wouldn't stop the game running.

Good luck!

---

### Post by Ripfox on 2007-06-14
Ok, now I did this:

@DualCore-Feisty:~$ sudo chown -R unclerusty:unclerusty /usr/var/tmp
Password:

@DualCore-Feisty:~$ cyphesis
2007-06-14 11:24:57 SCRIPT_ERROR /usr/lib/python2.4/whrandom.py:38: DeprecationWarning: the whrandom module is deprecated; please use the random module
2007-06-14 11:24:57 SCRIPT_ERROR   DeprecationWarning)
2007-06-14 11:24:57 INFO Running

Seems like I solved ONE problem, but I am still green at Linux, and have NO idea what the rest of that is.

Peace

---

### Post by mediax on 2007-06-15
Sorry, ripfox, but I've reached the end of my (very limited) expertise! :(

To my ignorant eye, it looks like the remaining errors you're posting shouldn't actually stop the program running - deprecation errors are normally advisory (telling the programmer to use more up to date code), rather than fatal.

You could see if anything's been posted into the event log - open /usr/var/tmp/cyphesis_event.log with a text editor and see what's there.

Good luck!

---

### Post by Ripfox on 2007-06-16
Yea, I gave up temporarily on this. It looks ok, but maybe not worth all this trouble :)

---

