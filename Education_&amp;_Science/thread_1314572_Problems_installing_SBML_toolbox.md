---
title: "Problems installing SBML toolbox"
date: 2009-11-04
forum: Education &amp; Science
---

### Post by Steeling on 2009-11-04
Hello friends

I run into a problem when installing SBMLToolbox-3.0.0 in a Ubuntu 9.10 x86_64
system. I have correctly installed libsbml, but when trying to 'make'
SBMLToolbox, I get the following messages:

mex -I/usr/local/include -I/usr/local/include/sbml  -I/usr/local/include  
-L/usr/local/lib OutputSBML.c -lsbml

Warning: You are using gcc version "4.4.1-4ubuntu8)".  The earliest gcc
version supported
         with mex is "4.1".  The latest version tested for use with mex is
"4.2".
         To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org) 

OutputSBML.c: In function ‘mexFunction’:
OutputSBML.c:220: warning: passing argument 1 of ‘SBase_setNotesString’
from incompatible pointer type
/usr/local/include/sbml/SBase.h:2269: note: expected ‘struct SBase_t *’
but argument is of type ‘struct Model_t *’
OutputSBML.c:234: warning: passing argument 1 of
‘SBase_setAnnotationString’ from incompatible pointer type
/usr/local/include/sbml/SBase.h:2289: note: expected ‘struct SBase_t *’
but argument is of type ‘struct Model_t *’
OutputSBML.c:294: warning: passing argument 1 of ‘SBase_setMetaId’ from
incompatible pointer type

[Many warnings follow, skipped]

/usr/local/include/sbml/SBase.h:2249: note: expected ‘struct SBase_t *’
but argument is of type ‘struct Delay_t *’

    mex: compile of ' "OutputSBML.c"' failed.

make: *** [OutputSBML.mexglx] Error 1


I would be very grateful if you can help me to solve this issue. 

Thank you very much!

---

### Post by Micronaut on 2009-11-18
I also have this problem.  I went into the make file and edited the mex location to explicitly point to my matlab folder (which is /home/user/matlab2009a/bin).  After this however I get:

make: execvp: /home/user/matlab2009a/bin: Permission denied
make: *** [OutputSBML.mexglx] Error 127

Tried to chown and chmod the directory but nothing works.  No idea how to progress.

edit: Ah, that might not help.  I changed the mex line to mex = /home/user/matlab2009a/bin/mex and it fails with the old error message again. Still no idea how to proceed.  


> **Steeling said:**
> Hello friends

I run into a problem when installing SBMLToolbox-3.0.0 in a Ubuntu 9.10 x86_64
system. I have correctly installed libsbml, but when trying to 'make'
SBMLToolbox, I get the following messages:

mex -I/usr/local/include -I/usr/local/include/sbml  -I/usr/local/include  
-L/usr/local/lib OutputSBML.c -lsbml

Warning: You are using gcc version "4.4.1-4ubuntu8)".  The earliest gcc
version supported
         with mex is "4.1".  The latest version tested for use with mex is
"4.2".
         To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org) 

OutputSBML.c: In function &#8216;mexFunction&#8217;:
OutputSBML.c:220: warning: passing argument 1 of &#8216;SBase_setNotesString&#8217;
from incompatible pointer type
/usr/local/include/sbml/SBase.h:2269: note: expected &#8216;struct SBase_t *&#8217;
but argument is of type &#8216;struct Model_t *&#8217;
OutputSBML.c:234: warning: passing argument 1 of
&#8216;SBase_setAnnotationString&#8217; from incompatible pointer type
/usr/local/include/sbml/SBase.h:2289: note: expected &#8216;struct SBase_t *&#8217;
but argument is of type &#8216;struct Model_t *&#8217;
OutputSBML.c:294: warning: passing argument 1 of &#8216;SBase_setMetaId&#8217; from
incompatible pointer type

[Many warnings follow, skipped]

/usr/local/include/sbml/SBase.h:2249: note: expected &#8216;struct SBase_t *&#8217;
but argument is of type &#8216;struct Delay_t *&#8217;

    mex: compile of ' "OutputSBML.c"' failed.

make: *** [OutputSBML.mexglx] Error 1


I would be very grateful if you can help me to solve this issue. 

Thank you very much!

---

### Post by GenghisKhan on 2009-11-20
I have the same problem. Please post here if you find a solution.

---

### Post by nateperson on 2009-11-20
I started to install it a bit ago, just to check it out, but stopped when I got the same error, mainly this part:> Warning: You are using gcc version "4.4.1-4ubuntu". The earliest gcc
version supported
with mex is "4.1". The latest version tested for use with mex is
"4.2".
To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org)

and didn't feel like working through it even though version 4.2 is in the repo's.  

Do ya'll get the same errors when trying to compile with version 4.2?

---

### Post by cezzar on 2009-12-23
Jaunty has a gcc version of 4.3. You should switch to eg.  gcc 4.2. Make sure it is installed; then you can make this older version active via:
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.2 /usr/bin/gcc


After you are done with toolbox installation; you can make gcc 4.3 active again by

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.3 /usr/bin/gcc

I guess this will help..

---

### Post by GenghisKhan on 2010-01-18
> **cezzar said:**
> Jaunty has a gcc version of 4.3. You should switch to eg.  gcc 4.2.

I tried it. It doesn't give out the warning about the compiler, but it still doesn't work.

---

### Post by nateperson on 2010-01-22
I found I needed to install SBMLToolbox for a project I'm working on, I got it working, but not easily, here are some pointers that should help.  BTW: These are not counting the compiler issues...

One, version of the dependencies.  This is a biggest one, even more so than when doing other manual installs on Linux of other softwares, and what version is required isn't always in a location that I think would be intuitive to find...

[INDENT]Example, from the news.txt of SBMLToolBox3.0.0 (why this isn't anywhere in the readme.txt I don't know) [/INDENT]
> Version 3.0.0



 - uses libSBML-3.1.0  Double check every dependency and its required version.

Two, I had to put it on a 32bit machine, there are apparently issues with older versions of libSBML on 64bit machines.  The 32bit I used machine happed to have Ubuntu 9.04 running on it and I didn't bother to upgrade

Three, make sure libSBML is installed properly and functioning first.  It's real finicky.  I never did get Java to work with it on a Ubuntu Linux box.  I almost installed fedora just so I could use the rpm...

Four, and I'm leaving this for last cause this is where I took the rest of the day off work after installing SBMLToolbox3.0.0:>   **Compatibility note**

A number of third-party MATLAB toolboxes use SBMLToolbox. *[COLOR="Red"]Beware that they may have restrictions on the version of SBMLToolbox with which they are compatible. For example, some are only compatible with version 2.0.2, not the current version 3 of SBMLToolbox.[/COLOR]* Please make sure to check the third-party software's documentation to determine which version of SBMLToolbox it needs
thats from  [http://sbml.org/index/Software/SBMLToolbox]("http://sbml.org/index/Software/SBMLToolbox") Its "below the fold" on the main site, I missed it the first time, So now I'm running SBMLToolbox2.0.2 and libSBML2.3.2.  So unless you're intent on 3.0.0....

Good luck, hope this helps.

---

### Post by saddamtohmto on 2010-12-28
Hello,

I am glad to see I am not the only one facing problems for installing SBML toolbox.

I have quite the same message than nateperson.

```
 make 
```gives me

```
/opt/matlab/bin/mex   -I/usr/local/include   -L/usr/local/lib OutputSBML.c -lsbml

Warning: You are using gcc version "4.4.3-4ubuntu5)".  The earliest gcc version supported
         with mex is "4.1".  The latest version tested for use with mex is "4.2".
         To download a different version of gcc, visit http://gcc.gnu.org 

```but nothing else!

And there is no OutputSBML.mexglx created in the toolbox.

What should I do?

Thx

---

