---
title: "&quot;cannot cd to /home/me&quot;"
date: 2006-02-10
forum: Desktop Environments
---

### Post by joehill on 2006-02-10
Something is really wrong with my system now.  I tried to install something using checkinstall and afterwards I lost all permissions to do anything.  It looks like checkinstall locked something but didn't unlock when finished.  If I type "ls" it says I don't have permission to execute /bin/ls, and the same goes for all commands, including sudo.  When I restart gdm doesn't start and I get the text login.  When I log in it says "cannot cd to /home/me."  I tried booting with a live CD and I can't find anything wrong with the permissions.  If I try running the same commands (./bin/ls, etc.) in the live CD environment they work fine.

Any ideas?  Thanks

Joe

---

### Post by zxee on 2006-02-10
I've had the same thing happen trying to use checkinstall in slackware.
I haven't fouled up my ubuntu install that way but in slack I found the solution was to open a shell/terminal and cd /home sudo chmod 700 me (if that's your personal directory name) sudo chown me me  chgrp me me  cd me 
chmod -R 777*  That worked for me, as I said in slackware. Hope that helps.

---

### Post by joehill on 2006-02-10
Thanks for the advice zxee.  Well, I figured it out and you're right that it was a permissions problem, although it wasn't a problem with my home directory (all my permissions seemed right and I couldn't log in as anyone but root).  I found the answer here after Googling the "no shell" error I got when trying to su to my own name: [http://www.sunmanagers.org/pipermail/summaries/2002-November/002656.html](http://www.sunmanagers.org/pipermail/summaries/2002-November/002656.html).

The problem was that the permissions on the root (/) directory had been set to 700, so after I chmoded / to 755 everything seems to have gone back to normal.  It appears that checkinstall does that to prevent concurrent filesystem changes from another program and if it doesn't exit correctly the permissions never get changed back.

---

### Post by easy_target on 2006-02-11
I am having exactly the same problem with the same origin: checkinstall. Can you please describe the steps in the command line to fix it?Thanks in advance.

---

### Post by joehill on 2006-02-18
Oops, I didn't check back here and see this reply until now.  You've probably either solved the problem or reformatted your hard drive by now, but I'll answer just in case anyone else happens to have the same problem.

In my case, checkinstall had apparently changed the permissions on / to 700 to freeze read/write on the whole system, although I could't actually see this because I don't know of a way of seeing the permissions if on / (maybe there's a way, but simply doing ls -l .. while in / gives the same result as typing ls -l / , listing the contents of / and not / itself).

So, suspecting that this must be the problem even though I couln't see it, I started up in rescue mode (you can't do it in normal mode because all commands, including sudo, ls, chmod, etc., are unreadable to all but root) and just did "chmod / 755".  That fixed everything.

---

