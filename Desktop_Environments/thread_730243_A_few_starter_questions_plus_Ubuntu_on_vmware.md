---
title: "A few starter questions plus Ubuntu on vmware"
date: 2008-03-20
forum: Desktop Environments
---

### Post by ubuntoexpert on 2008-03-20
OK I'm new to linux. I've just installed latest ubuntu on vmware server 1.0.3 and now want to install "vmware tools" and be able to vnc into it.

Can anyone tell me how to install vmware tools, I've done the vmware bit which mounts the iso image of vmware tools - but how do you install from there ? On the web there seemed to be lots of command line options but I can't even see how to start a command line session on ubuntu !!! Perhaps I have gone daft

What I want to get to is being about to access the ubuntu filesystem from external computers, and launch programs from external computers using rsh or similar. Any advice to help out getting me started there would be great.

---

### Post by jayson.rowe on 2008-03-20
To install vmware tools, go to VM- install VMWare Tools, and that should mount a virtual CD on your desktop, open that and copy the tar.gz file to your home folder.

Now, open your home folder, rightclick on that tar.gz file and select extract here.

Then, go to applications -> accessories and choose terminal.

once in terminal cd into the directory that was made by extracting the tar.gz (probably vmware-tools-install).

once in that directory "sudo ./vmware-install.pl"

and follow the on-screen instructions, and that should do it for you.

---

