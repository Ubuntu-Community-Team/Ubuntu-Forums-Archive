---
title: "[SOLVED] ./configure not working"
date: 2009-01-09
forum: General Help
---

### Post by prick.i.am on 2009-01-09
im tryin to profile an application. but when i type the command ./configure it says permission denied. What do i do?

---

### Post by dadozgb on 2009-01-09
> **prick.i.am said:**
> im tryin to profile an application. but when i type the command ./configure it says permission denied. What do i do?

sudo ./configure ?

---

### Post by Tim Sharitt on 2009-01-09
Make sure so have write permissions for the file and the directory it's in. If so, con figure may not be executable. To make it executable oopen a terminal an do:
```
chmod +x configure
```

---

### Post by prick.i.am on 2009-01-09
nope
i tried that...
didnt work....
The application is a linear program solver....
on windows i could run it..
but in linux i don know im not able to run it...
im tryin to optimize the code....

---

### Post by prick.i.am on 2009-01-09
tried that
it still says cannot find install-sh or install.sh

---

### Post by hyper_ch on 2009-01-09
> **dadozgb said:**
> sudo ./configure ?
there should not be any need to configure a source as root...

What program do you try to compile? What did you do so far?

---

### Post by prick.i.am on 2009-01-09
> **Tim Sharitt said:**
> Make sure so have write permissions for the file and the directory it's in. If so, con figure may not be executable. To make it executable oopen a terminal an do:
```
chmod +x configure
```

tried that
it still says cannot find install-sh or install.sh

---

### Post by binbash on 2009-01-09
> **dadozgb said:**
> sudo ./configure ?


dont do this.this is not a solution

---

### Post by prick.i.am on 2009-01-09
> **hyper_ch said:**
> there should not be any need to configure a source as root...

What program do you try to compile? What did you do so far?


The application is a linear program solver....
im not able to run it...
im tryin to optimize the code....

---

### Post by ajcham on 2009-01-09
> **prick.i.am said:**
> tried that
it still says cannot find install-sh or install.sh

Is the install script that it's looking for present?  If so make sure that is executable also:

```
chmod +x install.sh
```
or
```
chmod +x install-sh
```

---

### Post by prick.i.am on 2009-01-09
> **ajcham said:**
> Is the install script that it's looking for present?  If so make sure that is executable also:

```
chmod +x install.sh
```
or
```
chmod +x install-sh
```

actually its not my program
some one els program...
the install file is missing....

---

### Post by hyper_ch on 2009-01-09
> **prick.i.am said:**
> The application is a linear program solver...

and where can it be found?
does it have install instructios?

---

### Post by prick.i.am on 2009-01-09
> **hyper_ch said:**
> and where can it be found?
does it have install instructios?

i don find any install files...
no instructions either...
it jus has a read me file which says run "sh ccc" to build the program...

---

### Post by hyper_ch on 2009-01-09
you don't want to point out what that program is or where it can be found... well, in that case I can't do anything to help you.

---

### Post by lovelyvik293 on 2009-01-09
And so you have to try the 
```

sh ccc

```
The "ccc" must be install script.

---

### Post by LateNiteTV on 2009-01-09
is it a windows program? you said that you ran it on windows... so that leads me to believe that its a windows program and cant be run on linux.

---

### Post by prick.i.am on 2009-01-09
> **hyper_ch said:**
> you don't want to point out what that program is or where it can be found... well, in that case I can't do anything to help you.


dude chill... i wasnt pointing it out coz i myself am not sure of what exactly it does or wer its available...
one of ma buddies askd me if i can optimize it... tats it man... 
thx anyway... now its linear program solver as i earlier mentioned.
It is a free (see LGPL for the GNU lesser general public license) linear (integer) programming solver
based on the revised simplex method and the Branch-and-bound method for the integers.
It contains full source, examples and manuals.
lp_solve solves pure linear, (mixed) integer/binary, semi-continuous and
special ordered sets (SOS) models.

---

### Post by prick.i.am on 2009-01-09
> **lovelyvik293 said:**
> And so you have to try the 
```

sh ccc

```
The "ccc" must be install script.

yeah i did....
ccc is a build file...

---

### Post by prick.i.am on 2009-01-09
> **LateNiteTV said:**
> is it a windows program? you said that you ran it on windows... so that leads me to believe that its a windows program and cant be run on linux.

i don think tat must be the case..
it must be able to be run on linux...
i can build the application...
but im not able to configure and install it

---

### Post by mc4man on 2009-01-09
Is there a lp_solve directory or something similar? If so maybe cd to it and then run sh ccc

---

### Post by prick.i.am on 2009-01-09
> **mc4man said:**
> Is there a lp_solve directory or something similar? If so maybe cd to it and then run sh ccc

tats exactly how i did it.....
after i did tat der was a demo folder from wer i ran again another sh ccc..
den it showed me some results with varying no of variables and constraints.....
tat was not wat i wanted..
what i want is to be able to run the entire application, find out the hot spot, probably using gcov and gprof, then try to optimize it....

---

### Post by prick.i.am on 2009-01-09
> **hyper_ch said:**
> you don't want to point out what that program is or where it can be found... well, in that case I can't do anything to help you.

i first ran sh ccc from its directory.
after i did tat der was a demo folder from wer i ran again another sh ccc..
den it showed me some results with varying no of variables and constraints.....
tat was not wat i wanted..
what i want is to be able to run the entire application, find out the hot spot, probably using gcov and gprof, then try to optimize it....

---

### Post by forger on 2009-01-09
This program is in the repositories:
> 
lp-solve - Solve (mixed integer) linear programming problems
lp-solve-doc - Solve (mixed integer) linear programming problems - documentation


Execute this:
```

sudo apt-get install lp-solve lp-solve-doc

```

You can then use the program:
```

lp-solve

```

You can view the documentation:
```
firefox /usr/share/doc/lp-solve-doc/index.html
```

website:
[http://lpsolve.sourceforge.net/](http://lpsolve.sourceforge.net/)
[http://lpsolve.sourceforge.net/5.5/index.htm](http://lpsolve.sourceforge.net/5.5/index.htm)

---

### Post by prick.i.am on 2009-01-09
> **forger said:**
> This program is in the repositories:


Execute this:
```

sudo apt-get install lp-solve lp-solve-doc

```

You can then use the program:
```

lp-solve

```

You can view the documentation:
```
firefox /usr/share/doc/lp-solve-doc/index.html
```

website:
[http://lpsolve.sourceforge.net/](http://lpsolve.sourceforge.net/)
[http://lpsolve.sourceforge.net/5.5/index.htm](http://lpsolve.sourceforge.net/5.5/index.htm)

Can you plz tel me how to be able to run gcov or gprof on it?????

---

### Post by forger on 2009-01-09
nope, I have no idea, I just google-searched and found out about them:

[http://ccrma.stanford.edu/planetccrma/man/man1/gcov.1.html](http://ccrma.stanford.edu/planetccrma/man/man1/gcov.1.html)
[http://www.cs.utah.edu/dept/old/texinfo/as/gprof_toc.html](http://www.cs.utah.edu/dept/old/texinfo/as/gprof_toc.html)

---

### Post by LateNiteTV on 2009-01-09
how can you build it, but not configure and install it?

./configure is the first step in compiling it. if you cant even do that, then i have no idea how youre managing to "build" it.

```
./configure && make && make install
```

whats the name of the program thats giving you trouble?

---

### Post by prick.i.am on 2009-01-09
> **LateNiteTV said:**
> how can you build it, but not configure and install it?

./configure is the first step in compiling it. if you cant even do that, then i have no idea how youre managing to "build" it.

```
./configure && make && make install
```

whats the name of the program thats giving you trouble?

i built it using sh ccc from its directory

---

### Post by LateNiteTV on 2009-01-09
what program is it?

---

### Post by prick.i.am on 2009-01-09
> **LateNiteTV said:**
> what program is it?

its lp_solve...
i jus am not able to configure it..
i wanna run it wit gcov and gprof to analyze and profile the code....

---

### Post by LateNiteTV on 2009-01-09
oooooohhhhhh ok, so its already compiled and whatnot, correct? u can run the program?

./configure isnt for end user configuration.

./configure is for pre-compilation configuration of the make file.

---

### Post by prick.i.am on 2009-01-09
> **LateNiteTV said:**
> oooooohhhhhh ok, so its already compiled and whatnot, correct? u can run the program?

./configure isnt for end user configuration.

./configure is for pre-compilation configuration of the make file.

i get your point
but i don exactly follow you????
can you be lil more descriptive?
so if tats de case, how wud i be able toprofile it with gcov and gprof????

---

### Post by LateNiteTV on 2009-01-09
ive never used gcov or gprof. i dont know about those.

ok, say you download a source tarball or something. filename.tar.gz

you do: tar xvzf filename.tar.gz
this unzips and unpacks the file and creates a directory called filename.

now you cd into that directory. there will usually be a "configure" script. this is when you run: ./configure.

the ./configure command generates the "make file". the make file contains options for compilation. ./configure basically decides how the program is going to be compiled... "built".

you, as the user of the program, really have no control of the ./configure script. that is specifically designed by the programmer of the program to make sure that the program is compiled correctly.

---

### Post by prick.i.am on 2009-01-09
thx a lot buddy...
tats wat i was wondering wen i saw tat i already had makefile...

---

