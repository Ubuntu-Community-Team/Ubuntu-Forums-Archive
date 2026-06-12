---
title: "sudoers help!"
date: 2005-04-20
forum: Desktop Environments
---

### Post by redteto on 2005-04-20
I've modified my sudoers entering "visudo" at the prompt..

Now i can't anymore access as a root!

Help..

After the line: "root  ALL=(ALL) ALL" i added the line "myusername  ALL=(ALL) ALL" because i thought that this could give me root access even from my username..
Now if i enter at the prompt "sudo -s", the prompt returns: "myusername is not in the sudoers file. This incident will be reported."

What can i do??

---

### Post by syltty on 2005-04-20
Try advices from this link:
[http://ubuntuforums.org/archive/index.php/t-14366.html](http://ubuntuforums.org/archive/index.php/t-14366.html)

---

### Post by redteto on 2005-04-20
[QUOTE=syltty]Try advices from this link:
[http://ubuntuforums.org/archive/index.php/t-14366.html](http://ubuntuforums.org/archive/index.php/t-14366.html)[/QUOTE]

It works! I can enter the /etc/sudoers but i can't edit it anyway...when i try to save the file with ctrl^o the prompt return me: "Could not open file for writing: Read-only file system"...
Even if i try the command "visudo" i obtain as answer: "visudo: /etc/sudoers: Read-only file system"

 :???:  :???: 
Help..

---

### Post by redteto on 2005-04-20
Solved!!

But i had to insert the string "init=/bin/bash rw"
without the rw i couldn't modify anything...

---

