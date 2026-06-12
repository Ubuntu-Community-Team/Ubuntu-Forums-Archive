---
title: "SSH issue"
date: 2009-03-16
forum: General Help
---

### Post by Coding Monkey on 2009-03-16
Hi All

A week or two ago, I was tasked with writing a shell script to copy some files.  Some of the files are on a remote machine and I generated authentication keys and followed the steps in [http://linuxproblem.org/art_9.html]("http://linuxproblem.org/art_9.html").  Everything worked fine a week ago, and I could log in to the remote machine using ssh without a password, but when I tried to execute the script today, it asked for a password.  If I try to connect through the command line, outside of the script, I have the same problem.  

It looks like someone changed something on the remote machine, because when I tried to log in at the machine itself, I got a message saying something like "Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by others."

Does anyone have an idea how I can fix my ssh login problem?  Any help is much appreciated, thanks!

---

### Post by issih on 2009-03-16
I have vague memories of ssh autologon being flaky if anything unexpected was outputted to standard out during the logon. Not sure about that, but I think I remember a cluster I log onto having some form of hick up and just flat refusing to lamboot for a while.

I'd try to fix the error message on the host machine if I were you, and see if that helps..

[http://ubuntuforums.org/showthread.php?t=91455&page=4](http://ubuntuforums.org/showthread.php?t=91455&page=4)

The tail end of that thread might help.

---

### Post by Coding Monkey on 2009-03-16
Hi issih

Thank you for your reply.  I should have mentioned this earlier.  I've already fixed the error on the host machine, but that didn't solve the ssh issue.  Any other ideas?  Thanks.

---

### Post by issih on 2009-03-16
Not really, I'd just try removing the keys that don't work any more and regenerating them though. Chances are that whatever was done on the host machine has broken or invalidated the originals in some way, try making new ones?..

Hope that helps

---

### Post by Coding Monkey on 2009-03-16
Problem solved.  Thanks a lot issih!  In case anyone else runs into the same problem, I deleted the .ssh directories in the user's home folder on both machines and set up everything from scratch.

Stupid question - Is there anywhere that I can click to mark the thread as answered?

---

### Post by issih on 2009-03-16
The method changed at the same time the thanks button vanished..something to do with database corruption issues from various plugins that the forum software uses...

Apparently this is the approved of method now:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

:)


Glad you got it sorted.

---

