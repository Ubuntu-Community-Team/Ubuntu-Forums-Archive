---
title: "Bash completion"
date: 2004-12-08
forum: Desktop Environments
---

### Post by gfg on 2004-12-08
Dont know where else to post this so I post this here. Anyways I have heared about bash auto completion and i would like to know how to enable it. Thanks for the help!

---

### Post by OrangeSlice on 2004-12-08
It's enabled by default.  Type in a partial filename and hit the tab key.

---

### Post by oscarh on 2004-12-08
well, there is a file in /etc/ called bash_completion which is really useful.
try source /etc/bash_completion

of if you want it enabled by default you can edit either the system wide /etc/bash.bashrc or ~/.bashrc and uncomment the lines about bash_completion

---

### Post by kamstrup on 2004-12-08
OrangeSlice: Yes that is true. But with the bash_completion scripts you get intelligent auto completion. Ex "tar xzvf <tab>" only shows tar.gz and tgz files, not all files in the dir :) It is really nice.

---

