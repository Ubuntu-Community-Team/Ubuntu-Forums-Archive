---
title: "sudo kwrite error messages"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Princey on 2005-11-03
Hey guys, I need some advise here. I'm trying to mount my mtfs partition so I can access files on my Windows partition. However, when I call up kwrite using "sudo kwrite" minus the quotes of course, I get an error message:

Error: "/var/tmp/kdecache-prince" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-prince" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"


It does bring up kwrite after the error message but it's annoying anytime I sudo kwrite from the terminal. Any ideas of a work around? 

PS. Sorry if this is covered in another post. Searched for an hour but nothing close enough to what I'm looking for. Thanks in advance.

---

### Post by ajgreeny on 2005-11-03
Hi there Princey

Try using kdesu kwrite instead and I think all will be well.  This seems to be a kde thing rather than Ubuntu.  The same thing happens with kate and I found this answer for that a while ago on the forum.

Perhaps kdesu is neded for all or most root activities in kde; if sudo doesn't work I always try kdesu.  Give it a try!

---

### Post by Princey on 2005-11-03
[QUOTE=ajgreeny]Hi there Princey

Try using kdesu kwrite instead and I think all will be well.  This seems to be a kde thing rather than Ubuntu.  The same thing happens with kate and I found this answer for that a while ago on the forum.

Perhaps kdesu is neded for all or most root activities in kde; if sudo doesn't work I always try kdesu.  Give it a try![/QUOTE]

Thanks much for the info. It worked the first time churning a list of error messages. But when I went back to a pure prompt (was inside a folder) it worked without a glitch.:smile:

---

### Post by blastus on 2005-11-03
I also have had some nasty problems with pretty much everything; "sudo kwrite", "sudo kate", "kdesu kwrite", and "kdesu kate." See this thread: [Cannot edit text files in Kubuntu](http://ubuntuforums.org/showthread.php?t=80657). If all else fails, another command you can use to edit text files is "sudo nano." It is guaranteed to work everytime without weird problems!

---

