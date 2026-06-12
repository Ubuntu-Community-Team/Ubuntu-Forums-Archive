---
title: "Error msg's at boot. .dmrc file ignored"
date: 2010-07-28
forum: Desktop Environments
---

### Post by sptrsn on 2010-07-28
running Ubuntu 8.10
at boot I get the following error msg. 

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users'$home directory must be owned by the user and not writable by other users. 

I found what I think is that file. did a chmod 644 .dmrc and rebooted. Same error. 

System seems to run ok otherwise. 
Any help appreciated. 

steve

---

### Post by sptrsn on 2010-08-24
I found a tutorial on fixing this problem. worked great.
Thought I would share in case someone else finds this post before finding the tutorial. 
[http://ubuntuforums.org/showthread.php?t=976610&highlight=.dmrc+permission](http://ubuntuforums.org/showthread.php?t=976610&highlight=.dmrc+permission)

---

