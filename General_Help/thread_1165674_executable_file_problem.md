---
title: "executable file problem"
date: 2009-05-20
forum: General Help
---

### Post by jessedavis on 2009-05-20
Where to begin?  I have an executable file in a directory: jd/bin/prog. 

Working only in the directory that contains the file. (PATH environmental is correctly set and exported - although not needed) Distro has just been updated.

" ls -l "  tells me that permissions are 777 - anybody can do anything and that I am the owner. The GUI properties button returns, among other things, the fact that the file is an executable.  If I type the command line ./prog I get a message saying that the file does not exist. If I type just the file name at the prompt same thing happens. I can execute other files in this directory, just not this one!  Just for something to do I wrote hello.c, ran it through gcc with output in this directory. The executable runs OK.  So, why not this single program "prog"?

If I go to another directory and type just the file name the same thing happens.

_thanks in advance_.
jd

**[SIZE="5"]Death comes to those who wait.[/SIZE]**

---

### Post by mb_webguy on 2009-05-20
Typing "./*filename*" will only work if you're in the directory in which the file is located.  The "." means "this directory".  Try "~/bin/*filename*".  If that works, you need to add the bin directory to your path in order to be able to run the file by typing the filename.

In the terminal, enter the command "cat ~/.bashrc".  Look for the following section and make sure it looks like the below.```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
   PATH=~/bin:"${PATH}"
fi
```

---

### Post by jessedavis on 2009-05-21
Yes, well said.  I was in the directory the file was in and I also have the path variables set, verified by doing an echo $PATH from both this terminal installation and a separate invocation of terminal.

thx,
jd

---

### Post by geirha on 2009-05-21
Run the file command on it to see what type of file it is.
```
file ./prog
```

---

### Post by jessedavis on 2009-05-21
**_[SIZE="3"]file gives:[/SIZE]_**

[COLOR="Blue"]exu: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped[/COLOR]

**_[SIZE="3"]gdb answer:[/SIZE]_**

[COLOR="Blue"](gdb) run
Starting program: /home/jd/euphoria/bin/exu 
/bin/bash: /home/jd/euphoria/bin/exu: No such file or directory
/bin/bash: /home/jd/euphoria/bin/exu: Success

Program exited with code 01.
warning: Unable to find dynamic linker breakpoint function.
GDB will be unable to debug shared library initializers
and track explicitly loaded dynamic code.
You can't do that without a process to debug.

[/COLOR]

**_l[SIZE="3"]dd yields:[/SIZE]_**
	[COLOR="Blue"]not a dynamic executable[/COLOR]

[COLOR="Black"][/COLOR]
The error message is NOT coming from the shell.  It appears to be coming from the loader or the program itself.  Is there something required by exu to run on linux that is assumed to be there? 

[SIZE="4"]**Time marches onward toward the inevitable end.**[/SIZE]

---

### Post by geirha on 2009-05-21
Are you running 64bit Ubuntu perhaps? I see the executable is 32-bit, so it may be missing some 32-bit libraries ...

Installing [ia32-libs](apt:ia32-libs) might do the trick if that is the case.

---

### Post by jessedavis on 2009-05-22
**[SIZE="4"]Got it![/SIZE]**

I replaced Ubuntu 8 with Ubuntu 9 and the problem disappeared.  There was apparently a subtle bug.

Anyway, thanks for all your help.  I really appreciated it.

regards,
jd

**[SIZE="3"]And the dead shall awaken![/SIZE]**

---

