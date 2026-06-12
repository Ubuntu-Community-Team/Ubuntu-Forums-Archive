---
title: "where do programs go?"
date: 2009-01-26
forum: General Help
---

### Post by Armed Nuke on 2009-01-26
Hi, I know this is a stupid question but I have not studied linux very much. when i install epiphany or most programs from the repository where does ubuntu normally put them..and what is the usual file extension?

---

### Post by taurus on 2009-01-26
Most binaries/programs are located in /usr/bin.  

Applications -> Accessories -> Terminal
```
ls -la /usr/bin
```
And it doesn't have to have an extension or it can be any extension you want as long as it's a Linux binary or script file.

---

### Post by sancho panza on 2009-01-26
Since you mentioned about file extension, I assume you are asking about where on the hard drive those files are, and not where in the Applications menu they are listed?

Assuming I'm correct, any programs installed by synaptic are usually installed in various system folders. The executables (binaries) usually go into the /bin or /usr/bin folders and other relevant files (libraries, etc) go into other folder spread across the system. 
But all the config files (user settings) are stored in hidden folders in the user's home directory. More details about how linux files are setup can be found via wikipedia.

Cheers!

---

### Post by iaculallad on 2009-01-26
> **Armed Nuke said:**
> Hi, I know this is a stupid question but I have not studied linux very much. when i install epiphany or most programs from the repository where does ubuntu normally put them..and what is the usual file extension?

Actually, there are no file extensions if you're expecting to see *.exe files as what M$ winDoze applications usually do. Linux applications can be categorized as having their executable bit (+x) turned on.
Linux applications can be installed on places on your filesystem, your USR folder or BIN folder as an example.
You can manually search the location of an application installed by issuing the command below on the terminal (Applications->Accessories->Terminal):
```

which epiphany
```

or
```

which gedit
```

or 

```
which firefox
```

---

### Post by malfist on 2009-01-26
you can use the 'which' command to find out where the application is stored at.

Say if you're looking for where rsync is, you can do:
```

which rsync

```
And normally I believe it's stored at /usr/bin/rsync (but don't quote me).

---

### Post by Armed Nuke on 2009-01-26
thanks a lot guys. that is exactly what I needed to know. I could run epiphany or any installed program by typing it in the terminal but I did not know where it was. i searched through but could not find a collection of binarys. i know windows normally installed them in program files but I was unaware of where ubuntu was placing them.

---

### Post by mb_webguy on 2009-01-26
[This]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") should help you understand the Linux file structure a bit better.  Remember, Linux is not Windows -- but it does use some of the same basic ideas, such as storing all applications in one place (e.g. Program Files and /usr, respectively).  Once you understand what all of those oddly named directories are for, using Linux becomes considerably easier.

---

