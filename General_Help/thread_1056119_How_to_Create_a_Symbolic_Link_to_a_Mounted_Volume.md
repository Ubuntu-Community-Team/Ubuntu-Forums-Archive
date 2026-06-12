---
title: "How to Create a Symbolic Link to a Mounted Volume"
date: 2009-01-31
forum: General Help
---

### Post by DomIncollingo on 2009-01-31
I'm running Ubuntu (Intrepid) on two computers. I mounted my home directory from one computer on the other computer, and I'd like to create a symbolic link to it.

The home directory from second computer is mounted (via sftp) as:

[INDENT]*sftp://dji@linux/home/dji*[/INDENT]

I tried to make a symbolic link to this directory by running the command

[INDENT][I]ln -s sftp://dji@linux/home/dji  anotherHome
[/I][/INDENT]

But the link that is created (anotherHome) is not usable.  How can I create a symbolic link to a mounted volume?

Thanks very much.

Dom

---

### Post by Iowan on 2009-01-31
Somewhere in the foggy recesses that are what remains of my memory, I recall a limit on soft links not being able to "cross partitions", but I'll need to review to verify.

---

### Post by Rinzwind on 2009-01-31
[http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html](http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html)

I think (not tested myself) you need to mount it as a disk with NFS. 
That way you will have a directory to point ln to.

---

