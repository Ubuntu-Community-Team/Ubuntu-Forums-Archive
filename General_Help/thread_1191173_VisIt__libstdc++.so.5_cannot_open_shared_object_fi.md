---
title: "VisIt :::: libstdc++.so.5: cannot open shared object file: No such file or directory"
date: 2009-06-18
forum: General Help
---

### Post by lordhaworth on 2009-06-18
Hey all

I am trying to get visit working on Jaunty, I had previously managed to get it working on hardy with no issues. When i try to run it i ge tthe following message

"
thomas-laptop:~/visit/bin> ./visit
Running: gui1.11.2
/home/thomas/visit/1.11.2/linux-intel/bin/gui: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
"

I have tried creating the symbolic links as mentioned here:
[http://www.joewein.de/sw/swnotes002.htm](http://www.joewein.de/sw/swnotes002.htm)

But this does not correct the issue

Does anyone have any idea what I am missing? I have tried searching for it to no avail

Thanks

Tom

---

### Post by t4thfavor on 2009-06-18
Is the lib installed? I dont think it is by default.

---

### Post by lordhaworth on 2009-06-18
Do you know what library it is?

I've tried searching using the above in synaptic and sudo apt-get " " 

I think you are right in that its missing though

---

### Post by t4thfavor on 2009-06-18
Execute this command, I believe it should be one of these

apt-cache search libstd

More info here

[http://ubuntuforums.org/showthread.php?t=94740](http://ubuntuforums.org/showthread.php?t=94740)

Specifically 

"Thanks for the information..the libstdc++5-3.3-dev package you suggested did indeed have the libstdc++.so.5 library in it. Appreciate the help."

---

### Post by lordhaworth on 2009-06-18
Thanks very much that should get me to where I need to be

Impressive again ubuntu forums!

---

### Post by lordhaworth on 2009-06-18
To confirm, its working fine now - what you want in synaptic is

libstdc++5

Cheers

---

