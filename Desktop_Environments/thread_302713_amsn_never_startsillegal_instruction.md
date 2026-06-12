---
title: "amsn never starts:illegal instruction"
date: 2006-11-19
forum: Desktop Environments
---

### Post by nerubian on 2006-11-19
hello!
i reinstalled my ubuntu 6.10 system and everything is ok.i installed amsn 0.95 and due to the changes i2ve made in sources.list it upgraded to amsn 0.97.but when i tried to start, it hangs and then quits.when i try console, it gives me illegal instruction message.i installed tcl and tk 8.5 versions with amsn but it never starts.any help or solutions?

---

### Post by nerubian on 2006-11-19
i downloaded an amsn package file as said in one post, but i couldnt open with "sh" command.anyone knows what is the illegal instruction error?

---

### Post by lloyd_b on 2006-11-19
> i downloaded an amsn package file as said in one post, but i couldnt open with "sh" command.anyone knows what is the illegal instruction error?

"Illegal Instruction" means that the program tried to execute an instruction that isn't available on the current processor.  For instance, if you have a program compiled for Pentium 4, it will likely contain instructions that don't exist on a Pentium 3, so trying to run it on a P3 will get the "illegal instruction error".

What type of machine are you running on?  The default "amsn" package appears to be pretty generic.  

You don't "run" debian package files - you "install" them.  If you have a ".deb" file for amsn, then try the following command (in a terminal window):
```

dpkg -i {file}
```

Where {file} is the name of the file.

Lloyd B.

---

### Post by marcozs on 2006-11-20
I installed tcl/tk 8.5 and amsn 0.97b from Trevino's Repository ( [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) ) and I get the same error "Illigal Instruction". Running edgy...

---

### Post by nerubian on 2006-11-21
Lloyd B. thanks for the reply.i understand what you mean.package manager tries to install latest version and i get th error when i try to run amsn 0.97 (but it's actually the 0.96rc1).i deleted the the address which tries to upgrade amsn 0.95 to 0.97 from the /etc/apt/sources.list.finally, i downloaded the .deb package of amsn 0.96rc1 and i installed it manually.now it works.

---

### Post by nerubian on 2006-11-21
hmm.i followed the howto in this forum:[http://ubuntuforums.org/showthread.php?t=216689](http://ubuntuforums.org/showthread.php?t=216689) first i removed amsn and then downloaded tcl/tk 8.5 from the sources in this thread.i installed them now it works perfect.i think theres a problem with the sources i tried before, marcozs, same as your sources.

---

