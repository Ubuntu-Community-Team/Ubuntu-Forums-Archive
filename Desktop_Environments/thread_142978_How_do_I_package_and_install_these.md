---
title: "How do I package and install these?"
date: 2006-03-11
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-11
I have:
23 GTK2 themes that need to go into /usr/share/themes
11 Metacity themes that need to go into /usr/share/themes
4 icon themes that need to go into /usr/share/icons
5 gdm login themes that need to go into /usr/share/gdm/themes
17 gnome splash screens that need to go into /usr/share/pixmaps/splash
83 wallpapers that need to go into /usr/share/backgrounds

I want to do this so every user on the system can use these themes.

The easiest way I have found to install all of these themes is to:
1) Copy the theme tarballs to the proper directory
2) Untar the new theme tarballs
3) Delete the tarballs from the directory
4) Repeat the above steps for all themes

That is 15 steps in order to get all themes installed. What I would like to be able to do is package all these themes into one .deb file and perform one step to install them all:
1) sudo dpkg -i MyThemes.deb

There is no compiling involved at all, these are just themes. I have seen some how-to's about creating .deb's for Ubuntu 5.10 and they are blantanly over-complicated - all that is required is telling dpkg where all the files go.

Isn't there a simple way to create a .deb, that doesn't require compiling, for Ubuntu?

---

### Post by MichaelZ on 2006-03-11
Hello,

I asked one time how to do an ubuntu package. May be my thread could be useful or give some hints at least:

[http://www.ubuntuforums.org/showthread.php?t=140435]("http://www.ubuntuforums.org/showthread.php?t=140435")


Best wishes,
Michael

---

### Post by ardchoille on 2006-03-12
Thanks, but not much help. I would think that this wouldn't be so complicated since there is no compiling involved. Isn't there a step-by-step for building a .deb file? Would I be better off writing a bash script for this? Is there a way to make a tarball that will put the needed files in the correct places?

---

### Post by cwaldbieser on 2006-03-12
[QUOTE=ardchoille]Thanks, but not much help. I would think that this wouldn't be so complicated since there is no compiling involved. Isn't there a step-by-step for building a .deb file? Would I be better off writing a bash script for this? Is there a way to make a tarball that will put the needed files in the correct places?[/QUOTE]
I am not sure what your exact difficulties are.  

If you know that the folders these files are supposed to be installed to are exactly the same on each PC, you can have tar use the --absolute-names option.

I am not sure if this would work, but if I were going to try to make a simple .deb to do what you describe, I would create a folder for a project and dump all the tarballs in there.  Then I would try writing a simple makefile that would just extract the tarballs in the directories I wanted (maybe using the --directory option so I don't have to copy the tarballs there?).  I would make sure the makefile's "install" target would do this.  Then I would just try using "checkinstall -D".

---

### Post by ardchoille on 2006-03-12
How do I write a makefile? What is the syntax?
I don't have checkinstall installed. Is checkinstall required to build a .deb?

---

### Post by MichaelZ on 2006-03-12
Hello,

About make, this pdf book (zip compressed) could be useful:

[http://www.phptr.com/content/images/0130091154/downloads/0130091154.zip]("http://www.phptr.com/content/images/0130091154/downloads/0130091154.zip")

Best wishes,
Michael

---

### Post by cwaldbieser on 2006-03-12
[QUOTE=ardchoille]How do I write a makefile? What is the syntax?
I don't have checkinstall installed. Is checkinstall required to build a .deb?[/QUOTE]
checkinstall is a program that turns tarballs into .debs.  It is a somewhat quick-and-dirty way to make your own .debs (or rpms or other binary package formats).  It is not how the package maintainers do it, and I don't know enough about how Ubuntu packaging works to explain the differences.

A makefile is basically a text file.  Here is a quick example:
```

hello: hello.o
     gcc hello.o

hello.o: hello.c hello.h
     gcc -c hello.c

.PHONY: all clean install

all:  hello

clean:
     rm -f *.o hello

install:
     cp hello /usr/bin/local/hello
     chown root:root /usr/bin/local/hello
     chmod 711 /usr/bin/local/hello

```
What it says is that in order to build the **target**, hello, the **dependency**, hello.o, must be up to date.  In order to build hello.o, hello.c and hello.h must be up to date.  I also threw in some typical phony targets, "all", "clean", and "install".  The "all" target usually just has everything as a dependency, so everything gets built when you make it.  The "clean" target clears out intermediate files.  The "install" target usually copies the executables, etc. to where they are supposed to be installed.

Basic syntax is:

target target target: dependent dependent dependent
     command
     command
     command

(I used 3 or each, but there can really be any number).  There are a lot more complexities to make, but for simple makefiles, that's really most of what you need to know.

---

### Post by ardchoille on 2006-03-12
[QUOTE=MichaelZ]Hello,

About make, this pdf book (zip compressed) could be useful:

[http://www.phptr.com/content/images/0130091154/downloads/0130091154.zip]("http://www.phptr.com/content/images/0130091154/downloads/0130091154.zip")

Best wishes,
Michael[/QUOTE]
Thakn you, downloading the .pdf file now :)

---

### Post by ardchoille on 2006-03-12
[QUOTE=cwaldbieser]checkinstall is a program that turns tarballs into .debs.  It is a somewhat quick-and-dirty way to make your own .debs (or rpms or other binary package formats).  It is not how the package maintainers do it, and I don't know enough about how Ubuntu packaging works to explain the differences.

A makefile is basically a text file.  Here is a quick example:
```

hello: hello.o
     gcc hello.o

hello.o: hello.c hello.h
     gcc -c hello.c

.PHONY: all clean install

all:  hello

clean:
     rm -f *.o hello

install:
     cp hello /usr/bin/local/hello
     chown root:root /usr/bin/local/hello
     chmod 711 /usr/bin/local/hello

```
What it says is that in order to build the **target**, hello, the **dependency**, hello.o, must be up to date.  In order to build hello.o, hello.c and hello.h must be up to date.  I also threw in some typical phony targets, "all", "clean", and "install".  The "all" target usually just has everything as a dependency, so everything gets built when you make it.  The "clean" target clears out intermediate files.  The "install" target usually copies the executables, etc. to where they are supposed to be installed.

Basic syntax is:

target target target: dependent dependent dependent
     command
     command
     command

(I used 3 or each, but there can really be any number).  There are a lot more complexities to make, but for simple makefiles, that's really most of what you need to know.[/QUOTE]
Hmm.. checkinstall is in the repos, I'll install that and have a look at it. It could be that all I need to do this is to create my make file (using the .pdf posted by MichaelZ) and use checkinstall to create the .deb.. sounds promising :) Thank you.

---

### Post by ardchoille on 2006-03-12
well, make isn't working since there is no compiling needed in this project and checkinstall isn't working because there is nothing to "make". All the .deb needs to do is cp the graphics files to their spcified location.

Any ideas?

---

### Post by cwaldbieser on 2006-03-12
[QUOTE=ardchoille]well, make isn't working since there is no compiling needed in this project and checkinstall isn't working because there is nothing to "make". All the .deb needs to do is cp the graphics files to their spcified location.

Any ideas?[/QUOTE]
What does your makefile look like?  You should really just have an "install" target that untars the tarballs to the correct directory-- no compiling.  I did this once for a python program source someone wanted to make into a .deb.

Also, if you don't want to use make, checkinstall can accept any type of install script.  E.g.
```

$ sudo checkinstall -D my_install_script.sh

```

---

### Post by ardchoille on 2006-03-12
[QUOTE=cwaldbieser]What does your makefile look like?  You should really just have an "install" target that untars the tarballs to the correct directory-- no compiling.  I did this once for a python program source someone wanted to make into a .deb.[/QUOTE]
OK, I am just using the splashscreens as an example and here is my make file:
```

install:
	tar xzf splashscreens.tar.gz /usr/share/pixmaps/splash

```
so what do I do on the command line? checkinstall makefile=filename or what?

---

### Post by ardchoille on 2006-03-12
I tried using a bash script. The content of the bash script is:

```

#!/bin/bash
tar xzf splashscreens.tar.gz

```

The content of the tarball is:

/usr/share/pixmaps/splash/<various .png files>

The out put of: "$ sudo checkinstall -D install.sh" was

```

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: n

Installing with "install.sh"...

========================= Installation results ===========================
/var/tmp/iJpiYXgODoiRnUjPMbTD/installscript.sh: line 16: install.sh: command not  found

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I tried to look at /var/tmp/iJpiYXgODoiRnUjPMbTD/installscript.sh: line 16 and the file doesn't even exist.

What am I doing wrong?

---

### Post by cwaldbieser on 2006-03-12
[QUOTE=ardchoille]I tried using a bash script. The content of the bash script is:

```

#!/bin/bash
tar xzf splashscreens.tar.gz

```

The content of the tarball is:

/usr/share/pixmaps/splash/<various .png files>

The out put of: "$ sudo checkinstall -D install.sh" was

```

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: n

Installing with "install.sh"...

========================= Installation results ===========================
/var/tmp/iJpiYXgODoiRnUjPMbTD/installscript.sh: line 16: install.sh: command not  found

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I tried to look at /var/tmp/iJpiYXgODoiRnUjPMbTD/installscript.sh: line 16 and the file doesn't even exist.

What am I doing wrong?[/QUOTE]
I think maybe you just need to do:
```

$ sudo checkinstall -D ./install.sh

```
(I think the install script just needs to either be in your command path or you have to specify the path to it).

---

### Post by cwaldbieser on 2006-03-12
[QUOTE=ardchoille]OK, I am just using the splashscreens as an example and here is my make file:
```

install:
	tar xzf splashscreens.tar.gz /usr/share/pixmaps/splash

```
so what do I do on the command line? checkinstall makefile=filename or what?[/QUOTE]
With the makefile, it is easiest if you just name the makefile, "Makefile".  When you issue
```

$ sudo checkinstall -D

```
it will try to do a "make install" by default.

It may not make a big difference in your case, but you may want to change your makefile to include the .PHONY target:
```

.PHONY: install

install:
	tar xzf splashscreens.tar.gz /usr/share/pixmaps/splash

```

This is just a way to tell make that the install target isn't really a file (in case a file named "install" actually exists in the directory).

---

### Post by ardchoille on 2006-03-13
This command works beautifully:

```

$ sudo checkinstall -D tar xzf /path/to/tarball

```

I have to be in the dir that the package installs to but that is no big deal. It works. I have a .deb of my splashscreens - I tested it and it works great. Now, to package all the other themes I have.

Thank you cwaldbieser and MichaelZ for your knowledge and patience, you both are appreciated :)

---

