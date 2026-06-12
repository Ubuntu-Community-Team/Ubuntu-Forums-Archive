---
title: "Cannot change owner in hardy, root owns everything!"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by askander on 2008-04-28
Hi!!

I installed ubuntu 8.04 and I trying to run some shells and it always show in gedit, I try to change it to executable using nautilus (don't really know how to do it using the terminal) and root has all the permissions, I open a nautilus with this command

gksu nautilus

then, I can change the owner and permissions, but when I change the owner to my user account, it automatically changes to root again!! I don't know what to do to change this, at least I wanna run my scripts so I can do some work with my hardy install, how can I change them to executable?

Thanks in advance...

PD: When I type this in the terminal: "./shellname.sh" I get the "permission denied" message.

---

### Post by neptho on 2008-04-29
If your files are stored on a windows partition, you cannot change ownership to yourself, as it is.  They do not support the same functions as UNIX filesystems.

The reason you are getting 'permission denied' is because the file is not executable.  You need to set the 'execute' bit to make it run.  Here's the world's simplest rundown of how to do it in a terminal:

Make it so creator can read, write, and everybody can read/run:
chmod 755 <file>

Make it a 'normal' file that creator can change and others can read:
chmod 644 <file>

---

