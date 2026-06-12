---
title: "Problem with SBML Toolbox installation in Matlab"
date: 2008-09-04
forum: Education &amp; Science
---

### Post by pasQualle on 2008-09-04
It's me again.

Two days straight I'm trying now to install the SBML Toolbox in Matlab. And since the SBML forum won't let me in, I have to terrorize you with my questions.

I managed to install libsbml with the matlab extension by
```
sudo ./configure --with-matlab=/opt/matlabr2007a --with-bzip2=no
```

Why I have to skip bzip2? I don't know. Looking in the package manager, it's installed. But it's working this way. After the ```
make install
```
the following is output:
```
The installation of libSBML is finished.  On certain platforms
(such as Linux), you will also need to do one of the following:
1) run 'ldconfig' (see the man page if this is unfamiliar)
2) set the LD_LIBRARY_PATH (or equivalent) environment variable
```
The first I can do, what the second means I have no idea, so I didn't care.

Now I cd in the folder with the SBML Toolbox, do
```
export CFLAGS=-I/usr/local/include
export LDLAGS=-L/usr/local/lib

```
like said in the manual. And when I wanna execute the make file, the output is:
```
mex   -I/usr/local/include   -L/usr/local/lib OutputSBML.c -lsbml
make: mex: Command not found
make: *** [OutputSBML.mexglx] Error 127
```
But I think mex is installed and in the right folder. The thing that confuses me (and I also think this is the reason why it's not working), is that if I tpye in ```
which mex
``` it gives me 
```
/opt/matlabr2007a/bin//mex
```
So there are two slashes. Why? Stupid machine!
I looked in the .bashrc if there's the right path and also in the matlab path.

Has anybody of you successfully installed the SBML Toolbox for Matlab? Or does anybody knows how to solve my problems?

I really need help here.
Thanks in advance!!!

---

### Post by biomystery on 2009-02-25
I suggest you try to edit the Makefile file.

change the line
"MEX       = mex"

into 

"MEX       = /usr/local/matlab/bin/mex", i.e. add the path where your mex locate.

Then, try make again.

Good lucks.

---

### Post by Dott.MattiX on 2010-10-04
> **biomystery said:**
> I suggest you try to edit the Makefile file.

change the line
"MEX       = mex"

into 

"MEX       = /usr/local/matlab/bin/mex", i.e. add the path where your mex locate.

Then, try make again.

Good lucks.

I've the same problem...
any news?

i've tried to change the path but it doesn't work


(sorry for my english :D )

---

### Post by nateperson on 2010-10-06
I've had SBML toolbox installed in the past...  It wasn't easy to do though, and I don't remember all the steps and issues I had, but will help with what I can.

1.)> 2) set the LD_LIBRARY_PATH (or equivalent) environment variable
    This is very important.  I added mine to my .bashrc, otherwise you have to reset it every time. so you add, ```
export LD_LIBRARY_PATH=/some/path/somewhere:$LD_LIBRARY_PATH
```
Can't remember what path is supposed to go in there, but basically it needs to know where the libSBML libraries are at...  so probably is /usr/local/lib.  

I'd add these in the .bashrc too: ```
export CFLAGS=-I/usr/local/include
export LDLAGS=-L/usr/local/lib
```

2.) I had a lot of issues with versions and compatibility. Here's a thread on SBML Toolbox with some comments from me on on it, about my version and compatibility woes: [http://ubuntuforums.org/showthread.php?t=1314572]("http://ubuntuforums.org/showthread.php?t=1314572")

Good luck on your installation.

---

