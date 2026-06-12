---
title: "weird gcc and PATH problem"
date: 2005-06-15
forum: Desktop Environments
---

### Post by davegod75 on 2005-06-15
I'm trying to install the VMWARE 5 trial.  I'm getting an error near the very end of the install.  It says it can't find gcc

so I do a "which gcc' and nothing.  It doesn't show up.

I do have gcc-3.3 installed in /usr/bin.  I can cleary see it.  I also have both the gcc-base and gcc packages.

my $PATH is: 
bash: /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

any ideas on how to fix this problem?

Thanks?

---

### Post by Klin'Targ on 2005-06-15
make sure you have execute permission on gcc, and that /usr/bin/gcc exists (not just /usr/bin/gcc-3.3). If it doesn't exist, you could symlink it to fix the problem (not sure why this would happen in the first place though...)

---

