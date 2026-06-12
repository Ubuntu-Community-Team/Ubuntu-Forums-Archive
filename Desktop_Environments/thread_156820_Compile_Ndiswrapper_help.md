---
title: "Compile Ndiswrapper help"
date: 2006-04-07
forum: Desktop Environments
---

### Post by joplass on 2006-04-07
Below are instructions I found while compiling ndiswrapper on a friend's computer.  Just one clarification I need if the say go to source in the example what source do they mean?  Full page: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Compile_and_install](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Compile_and_install)

Compile and install
Go to source-directory and do

make distclean

As root run

make

and then

make install

---

### Post by taurus on 2006-04-07
Source directory is the program that you've downloaded.  For instance, let's say you download bug_bunny.tar.gz, then you first need to unpack it before to can change to the source directory as
```

tar xvzf bug_bunny.tar.gz

```
That will create a directory of bug_bunny and THAT is your source directory...
```

cd bug_bunny

```

---

### Post by joplass on 2006-04-08
thansk it worked :-D

---

### Post by taurus on 2006-04-08
[QUOTE=joplass]thansk it worked :-D[/QUOTE]
You're welcome.  ;)

---

