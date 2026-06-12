---
title: "How to install Nvidia drivers on Ubuntu 8.10"
date: 2009-05-06
forum: General Help
---

### Post by mdp25 on 2009-05-06
I’m having trouble loading an Nvidia graphics driver on Ubuntu 8.10.  I’m a long time Windows user new to Linux so I’m sure this is a simple fix.  I downloaded the latest driver from Nvidia (Nvidia-Linux-x86-180.51-pkg1.run) using my XP machine.  As instructed, from a terminal window I entered "sh NVIDIA-Linux-x86-180.51-pkg1.run".  Everything seems to work for a few seconds then an Nvidia error message pops up saying the install must run as root.  I’m not really sure how to install as root in Ubuntu.  I tried typing “sudo su” then the same install procedure but nothing happens.

Any help would be great.  

By the way this machine is not on the internet so I can’t do the automatic update that other posts have recommended.

Thank you!

---

### Post by Kareeser on 2009-05-06
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44) :)

Careful when you drop down to tty1 using Ctrl-Alt-F1, since you won't have access to a GUI. Write down all of the steps!

---

### Post by mdp25 on 2009-05-06
Now that's service...What did that take, 5 seconds.  I'll give these instructions a try.

Thank you Kareeser!

---

### Post by exutable on 2009-05-06
Can't you just log in as root too using sudo -i?

and then running the command?

---

### Post by Snyper450 on 2009-05-06
Your drivers shoudl allready be installed thou if you go to the proprietary drivers bit and see if its activated??

---

### Post by Kareeser on 2009-05-07
> **exutable said:**
> Can't you just log in as root too using sudo -i?

and then running the command?

Unfortunately, no, the nvidia script requires that the X window manager be shut down, in addition to being run as root.

Someday, that might change, but not today :)

---

