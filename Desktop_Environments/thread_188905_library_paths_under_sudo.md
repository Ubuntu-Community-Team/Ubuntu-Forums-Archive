---
title: "library paths under sudo"
date: 2006-06-04
forum: Desktop Environments
---

### Post by paulyche on 2006-06-04
I want to edit my LD_LIBRARY_PATH variable to include another dir. I'd normally put changes in my .bashrc. However, the command I want to run needs to be ran as root via sudo. 

How can I change variables for all users / or for the root user?

---

### Post by rbalfour on 2006-06-04
edit 

/etc/bash.bashrc

Systemwide file for bash.

---

### Post by paulyche on 2006-06-04
Thanks rbalfour,

To anyone else reading this I edited a /etc/bash.bashrc and put this at the top:
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib/

I wanted to add /usr/local/lib/ to the list of directories in LD_LIBRARY_PATH. so the line above means make LD_LIBRARY_PATH equal what directories were defined there before and also add /usr/local/lib/

---

