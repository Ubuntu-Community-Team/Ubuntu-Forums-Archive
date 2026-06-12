---
title: "Where are all the programs?"
date: 2005-09-17
forum: Desktop Environments
---

### Post by MattVonFat on 2005-09-17
Ok, so from this you are going to tell that i am primarilly a Windows user. I need to add a file to the directory that i installed something to. But i don't know where these things would install to. On Windows its obviously C:/Program Files but i am very new with Linux and i haven't a clue where to look. Can anyone help?

---

### Post by cwaldbieser on 2005-09-17
[QUOTE=MattVonFat]Ok, so from this you are going to tell that i am primarilly a Windows user. I need to add a file to the directory that i installed something to. But i don't know where these things would install to. On Windows its obviously C:/Program Files but i am very new with Linux and i haven't a clue where to look. Can anyone help?[/QUOTE]
Typically, software that you install for system wide use gets put in several directories:

/usr/bin -- binaries & executables
/usr/lib -- libraries
/usr/share  -- supporting resource files

For stuff not directly associated with your distro, the files are sometimes placed in :
/usr/local/bin
/usr/local/lib
/usr/local/share

And of course, software can be installed non-system wide in any folders you have permissions for.

From synaptic, you can find a list of every file from a package and where it was installed by going to the Properties for the package.  Alternatively, you can type:
```
$ dpkg -L 'package-name'
``` 

It is also important to note that in many cases, you can customize the behavior of programs without having to add files to where they were installed.  Sometimes you can just create a symbolic link.  In lots of cases, you can set an option in a local configuration file (usally a hidden "dot-file" in your home directory) to use resource files in the folder you choose.

---

### Post by mcmuffy on 2005-09-17
If you installed your program using synaptic (or something similar) then select the program and hit properties. It should tell you what files were installed where.

---

