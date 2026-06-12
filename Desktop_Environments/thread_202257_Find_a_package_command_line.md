---
title: "Find a package command line"
date: 2006-06-23
forum: Desktop Environments
---

### Post by danielph on 2006-06-23
A simple (maybe stupid) question. I often switch between apt-get and synaptic using synaptic to search the repos for a package. Can I search for a package from the command line?

thanks

Dan

---

### Post by loell on 2006-06-23
apt-cache search <package_name>

---

### Post by danielph on 2006-06-23
thanks,

I thought it was something simple

---

### Post by angkor on 2006-06-23
apt-cache has lots of useful utilities. From the man page:

```
apt-cache is a low-level tool used to manipulate APT's binary
cache files, and query information from them

Commands:
   add - Add a package file to the source cache
   gencaches - Build both the package and source cache
   showpkg - Show some general information for a single package
   showsrc - Show source records
   stats - Show some basic statistics
   dump - Show the entire file in a terse form
   dumpavail - Print an available file to stdout
   unmet - Show unmet dependencies
   search - Search the package list for a regex pattern
   show - Show a readable record for the package
   depends - Show raw dependency information for a package
   rdepends - Show reverse dependency information for a package
   pkgnames - List the names of all packages
   dotty - Generate package graphs for GraphVis
   xvcg - Generate package graphs for xvcg
   policy - Show policy settings
```

I mainly use 'search', 'show', 'policy' and 'depends'.

apt-get also has got quite a few options:

```
apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
```

---

### Post by loell on 2006-06-23
[QUOTE=danielph]thanks,

I thought it was something simple[/QUOTE]

actually its that simple, its not just package name you can search you can also search for keyword :)

also try the command

      aptitude search The_keyword_or_package_name

::)

---

### Post by danielph on 2006-06-23
A whole new world of commands, thanks. I didn't even know apt-cache existed.

As for aptitude, just one thing, I could not work out the key for the packages with aptitude search. It shows p, i, c, v, ip etc. I am guessing i = installed?

---

### Post by loell on 2006-06-23
yes, i guess so :)

i'm newbie too when it comes to aptitude...

---

