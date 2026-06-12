---
title: "removing apps not installed with synaptic or apt"
date: 2006-07-05
forum: Desktop Environments
---

### Post by JPMaximilian on 2006-07-05
I installed the ipodlinux installer onto my 6.06 machine using the following commands:

wget -P /tmp [http://www.rit.edu/~rmh3093/installer2/2.2/ipodlinux-installer-2.2l.run.gz](http://www.rit.edu/~rmh3093/installer2/2.2/ipodlinux-installer-2.2l.run.gz)
gunzip /tmp/ipodlinux-installer-2.2l.run.gz
chmod +x /tmp/ipodlinux-installer-2.2l.run 

then sudo ipodlinux-installer-2.2l.run

How would I got about uninstalling this?

---

### Post by ionophore on 2006-07-05
Well assuming that you were logged in as a regular user at the time, the only possible place it could have installed itself to is some place within your home dir, so i would just do an

ls -l

in your home dir, figure out where it put itself, and delete the appropriate folder/files.  

Of course, if you were root/sudo when you installed it you'll have to check the documentation to see exactly what files it dropped where...

-ben

[edit]  Oops, i see that you did use sudo to install it.  You will have to check the docs that came with it (or perhaps check the developer's website) to see exactly what that installer does.  Once you figure it out though it is most likely just a matter of removing files.

---

