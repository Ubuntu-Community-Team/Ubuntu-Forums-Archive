---
title: "Can't add to Starup Programs"
date: 2007-07-13
forum: Desktop Environments
---

### Post by gardenlevel on 2007-07-13
Help!

I'm trying to add programs to my startup but they won't stay added. I enter my program (in this case beryl-manager) hit close and when I reopen Sessions it's gone.

---

### Post by zanglang on 2007-07-13
Maybe you've accidentally run Sessions as root previously, so now you're not allowed to make any modifications to it? Try running
> gnome-session-properties
from the command line, and see if it shows any odd error messages. If it says something similar to "unable to saving" files, try this:
> sudo chown -R <your user name> ~
sudo chmod -R o+rw ~

---

### Post by gardenlevel on 2007-07-13
That solved it, Thanks.

---

### Post by ztirffritz on 2007-08-27
I'm so impressed with the community support in Ubuntu.  It took me all of 2 minutes to find the solution to this problem, and it solved the problem on 3 computers.  Thanks.

---

