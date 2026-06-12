---
title: "How do I manually run 'dpkg --configure -a?"
date: 2006-05-29
forum: Desktop Environments
---

### Post by leica on 2006-05-29
I download taskjuggler with apt from one of the standard repositories that are recommended.  Something happened during the installation and taskjuggler was not installed properly.  I tried to reinstall the program and the reinstall did not work.  I tried to remove taskjugger and the follow message was displayed,"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."  How do I manually run 'dpkg --configure -a?

Thank you for you help in advance.

---

### Post by hw-tph on 2006-05-29
You type **sudo dpkg-reconfigure -a**. This will reconfigure all packages so it will take a very long time.


Håkan

---

### Post by Hanj on 2006-05-29
Chose Applications->Accessories->Terminal, in case you didn't know where to type it.

---

### Post by Paintrick on 2006-05-30
I believe you will end up with the same problem I had, check the topic here:

[http://www.ubuntuforums.org/showthread.php?t=177538](http://www.ubuntuforums.org/showthread.php?t=177538)

---

### Post by Sukarn on 2006-05-30
[QUOTE=hw-tph]You type **sudo dpkg-reconfigure -a**. This will reconfigure all packages so it will take a very long time.


Håkan[/QUOTE]
"sudo dpkg --configure -a" is enough, usually. You dont usually have to perform "sudo dpkg-reconfigure -a"

---

