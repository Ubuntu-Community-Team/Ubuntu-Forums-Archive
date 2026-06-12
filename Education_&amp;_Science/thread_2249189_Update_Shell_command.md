---
title: "Update Shell command"
date: 2014-10-20
forum: Education &amp; Science
---

### Post by mahmoud7 on 2014-10-20
Hi,
How I can access the source code of shell commands? then update it?

---

### Post by Lars Noodén on 2014-10-20
They are all shell "commands"  Which program are you interested in?  You will need to know which package it is part of.  Then, if you have the package 'build-dep' already installed, you can use apt-get to fetch the source.  Here is how you could do it for the package 'tidy'

```

cd /tmp/
apt-get source tidy

```

That will put all the source materia for the package 'tidy' in the directory /tmp where you can work on it and then build a new package.

---

### Post by mahmoud7 on 2014-10-20
the question in another words; how i can for example see the source code of **cp **command? 
how i can modify it?

---

### Post by TheFu on 2014-10-20
> **mahmoud7 said:**
> Hi,
How I can access the source code of shell commands? then update it?

Lars could be interpreting this correctly or perhaps you just want to edit a shell script?  If the script was installed through a package via the package manager, then follow what Lar's says above.  Modifying the commands used inside most shell scripts is something left to a C programmer, almost always.  Most commands called by shell scripts are located in /bin or /usr/bin and are compiled C programs.

OTOH, you may not want to alter any compiled programs and just want to tweak the script itself?  If the script is located somewhere on the system - use "which {name-of-program}" to find where it is and edit away. It is a good idea to make a backup of the file before you start and to not make the changes for everyone on the system - just for you by renaming the script and putting it into your personal ~/bin/ directory.  At least until it has been thoroughly tested.  Most pre-installed programs on a system are used by many other tools on the system, so altering the behavior is not a good idea.

If you can clarify more about this, Lars and I can be helpful - probably.

Update - seeing the posts below this one - seems like Lars understood the desire perfectly.

---

### Post by Lars Noodén on 2014-10-20
For 'cp' you need to find out which package it is in:

```

dpkg -S /bin/cp

```

That shows it is in 'coreutils', so you can grab the source for coreutils.  Here is how it would be for Ubuntu 14.04.1 LTS:

```

cd /tmp/
apt-get source coreutils
cd coreutils-8.21/

```

That assumes you also have the packge 'dpkg-dev' already installed because you need it for working with the source packages.  

Then you can look around in that directory for the source for 'cp'.

---

### Post by matt_symes on 2014-10-20
Hi

Just a addendum to what Lars said - and assuming you want to play with a bit of C code - you may want to check if the command is a shell builtin or not.

```

matthew-laptop:/home/matthew:7 % type echo
echo is a shell builtin
matthew-laptop:/home/matthew:7 % type cp
cp is /bin/cp
matthew-laptop:/home/matthew:7 % 
```

Kind regards

---

### Post by TheFu on 2014-10-20
I hadn't looked at the C code for this stuff in ... er ... 20+ yrs.  It has changed!

cp.c --> do_copy() --> copy.c --> copy_reg() to handle the real byte-by-byte stuff (generally - there are many other paths possible).

Lots of stuff around permissions, SElinux, links, symlinks, acls, recursive dirs ---- very interesting.  Interesting to see they optimize for the memory page size and recognize performance issues with really deep recursive copies.

Personally, I'd be afraid to alter this code ... I'm more likely to modify the kernel network driver to modify things coming or going on the wire (which I've done before). ;)  That code actually modified my resume text and I'd forgotten my driver changes were still active.  It replaced a commonly known computer OS vendor corporate name with a commonly used, non-flattering version. Not good for the job search.

Anyway - excellent question and good, helpful, answers. Very cool!

---

### Post by mahmoud7 on 2014-10-27
thanks you all, i had access the source code and add printf statement to its main function. 
now how i do compile so when run command it will print the statement ?

---

### Post by matt_symes on 2014-10-28
Hi

> **mahmoud7 said:**
> thanks you all, i had access the source code and add printf statement to its main function. 
now how i do compile so when run command it will print the statement ?

Install the build-essential package to start with

```
sudo apt-get install build-essential
```

Then read the file INSTALL in the coreutils root directory.

Install any dev dependencies required then run 'configure' with the required options and 'make'. 

I would set the install path as /opt or /usr/local if you are going to 'make install' and use the full path to call the binaries to keep then separate from your distributions binaries.

Kind regards

---

