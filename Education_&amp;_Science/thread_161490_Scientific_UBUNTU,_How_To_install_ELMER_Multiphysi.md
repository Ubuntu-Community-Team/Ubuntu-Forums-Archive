---
title: "Scientific UBUNTU, How To install ELMER Multiphysics"
date: 2006-04-17
forum: Education &amp; Science
---

### Post by derjames on 2006-04-17
**How To install ELMER Multiphysics software**

Following my previous thread about installing OpenFOAM, 

[http://ubuntuforums.org/showthread.php?t=156298](http://ubuntuforums.org/showthread.php?t=156298)

now is time for ELMER, this software is an ideal complement to OpenFOAM, ELMER also uses finite element to solve Partial Diferential Equations which are applied to numerous scientific and engineering problems,   So here we go

**System requirements**

Athlon/Pentium other similar (but also supports other architectures)
Memory 640 MB (well my PC has that amount, you've got to test in yours)
200 MB Hard drive  (the installation takes aprox 150 MB)
LINUX Ubuntu 5.10 Breeze Badger Kernel version 2.6.12-9-386 (I don't know what would happen with another version, just test and tell me)
Good DJ music (i.e. Paul Van Dyk) to listen while you install this nice piece of software

**Download the tar.gz file from**

[http://www.csc.fi/elmer/download/](http://www.csc.fi/elmer/download/)

This is binary file version 4.0, the version 5.0 is not compiled yet, however you can download the source as well from that page, the method I describe here is about installing version 4.0, I did try to compile ver 5.0 but I had some problems with libraries which are not updated or something like that, I will try to work in the future on that, I can say Ver4.0 seems robust enough for my needs. Before starting remember that LINUX is Case sensitive

Now consider installing ELMER on your home directory, for example mine is

```
/home/james  or  ~/  
```

(important: change 'james' for your user name)
you can select any other, though, just change the PATH and environment variables accordingly, now copy the file tar.gz to your home directory and untar it

you will see a new directory

[COLOR="Blue"]~/ELMER4.0[/COLOR]

Now you have to update the following shell scripts

[COLOR="Blue"]~/ELMER4.0/bin/ElmerFront
~/ELMER4.0/bin/ElmerPost
~/ELMER4.0/bin/ElmerSolver
~/ELMER4.0/bin/GebhardtFactors[/COLOR]

Open each file and save them as xxxxx-backup, to have a copy of the original file just in case you need it in the future

now open ElmerFront (double click in its icon), you will see the contents displayed on gedit
the first you will notice is that the script is writen in C-shell, if you have Ubuntu with csh or similar you don't need to do nothing more

if you are using Ubuntu with the default configuration (like me) then your shell is BASH, type echo $SHELL if you are not sure, if this is true, put a hash to every single line or delete them, they are not needed anymore and write

**for ElmerFront * * * * * * * * **

```
#!/bin/bash -f

#Setting environment variables, change accordingly

export ELMER_HOME=/home/james/ELMER4.0
export ELMER_FRONT_HOME=$ELMER_HOME/Front
export TK_LIBRARY=$ELMER_HOME/lib/tk8.3
export TCL_LIBRARY=$ELMER_HOME/lib/tcl8.3

export PATH=$PATH:$ELMER_FRONT_HOME/tcl
export PATH=$PATH:$ELMER_HOME/bin
export PATH=$PATH:$ELMER_HOME/lib
export PATH=$PATH:$ELMER_HOME/Front
export PATH=$PATH:$TK_LIBRARY
export PATH=$PATH:$TCL_LIBRARY

#The following lines assume you are using LINUX on a x86 system
#for a different system contact [http://www.csc.fi/elmer](http://www.csc.fi/elmer)
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

$ELMER_HOME/bin/ld.so --library-path .:$ELMER_HOME/bin:$ELMER_HOME/lib \
$ELMER_HOME/bin/Front $*
```

**for ElmerPost type * * * * * * * * * * * *** 

```
#!/bin/bash -f
#Setting environment variables, change accordingly

export ELMER_HOME=/home/james/ELMER4.0
export ELMER_POST_HOME=$ELMER_HOME/post
export MESA_BACK_BUFFER Pixmap
export TK_LIBRARY=$ELMER_HOME/lib/tk8.3
export TCL_LIBRARY=$ELMER_HOME/lib/tcl8.3

export PATH=$PATH:$ELMER_HOME/bin
export PATH=$PATH:$ELMER_HOME/lib
export PATH=$PATH:$ELMER_HOME/Front
export PATH=$PATH:$TK_LIBRARY
export PATH=$PATH:$TCL_LIBRARY

#The following lines assume you are using LINUX on a x86 system
#for a different system contact [http://www.csc.fi/elmer](http://www.csc.fi/elmer) or see original ElmerPost file
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

$ELMER_HOME/bin/ld.so --library-path .:$ELMER_HOME/bin:$ELMER_HOME/lib \
$ELMER_POST_HOME/bin/i386-linux/ElmerPostGL $* £


```

**for ElmerSolver type the following * * * * * * * * * * * * * * * * *** 

```
#!/bin/bash -f

export ELMER_HOME=/home/james/ELMER4.0
export TK_LIBRARY=$ELMER_HOME/lib/tk8.3
export TCL_LIBRARY=$ELMER_HOME/lib/tcl8.3

$ELMER_HOME/bin/ld.so --library-path .:$ELMER_HOME/bin:$ELMER_HOME/lib \
$ELMER_HOME/bin/ElmerSolver.bin


```

**and for GebhardtFactors type the following * * * * * * * * * * * * * ***

```
#!/bin/bash -f

export ELMER_HOME=/home/james/ELMER4.0
export TK_LIBRARY=$ELMER_HOME/lib/tk8.3
export TCL_LIBRARY=$ELMER_HOME/lib/tcl8.3

$ELMER_HOME/bin/ld.so --library-path .:$ELMER_HOME/bin:$ELMER_HOME/lib \
$ELMER_HOME/bin/GebhardtFactors.bin

```

now change each script to executable mode using 

```
chmod -v 555 xxxxx
```

where xxxxx is the name of the shell script

If you try to launch ELMER at this point, it will call some libraries that are not in your PC these are

[COLOR="Blue"]libMesaGL.so.3
libMesaGLU.so.3
libtk8.3.so
libtcl8.3.so
[/COLOR]

however Ubuntu has others that are completely compatibles with them

[COLOR="Blue"]libGL.so.1.2
libGLU.so.1.3.060302
libtk8.4.so.0
libtcl8.4.so.0
[/COLOR]

which are located at /usr/lib  although it can be other location (just look for them)

what you have to do is to create a symbolic link to point to these libraries when ELMER call the old ones, so type

```
ln -s /usr/lib/libGL.so.1.2 /usr/lib/libMesaGL.so.3
ln -s /usr/lib/libGLU.so.1.3.060302 /usr/lib/libMesaGLU.so.3
ln -s /usr/lib/libtk8.4.so.0 /usr/lib/libtk8.3.so
ln -s /usr/lib/libtcl8.4.so.0 /usr/lib/libtcl8.3.so

```
[B]
Modifying environment variables * * * * * * * * *[/B] 

create the following hidden directory

[COLOR="Blue"]~/ELMER4.0/.ELMER4.0[/COLOR]

there, create the following file 'bashrc' and type

```

#!/bin/bash -f
export PATH=$PATH:~/ELMER4.0/bin

```

save and quit

now modify .bashrc which is located in your home folder, use gedit or vim as usual

```
gedit ~/.bashrc &
```

type at the end of the file

```
. ~/ELMER4.0/.ELMER4.0/bashrc
```
N.B. it is "dot", "space" ....

save and exit

Now type in terminal

```
. ~/.bashrc
```

to update the environment variables

and type 

```
echo $PATH
```

to see the changes (the path to ELMER4.0 is shown)

And it's done!!, you can start modelling right away!, well just after a bit of reading!, documentation is not included in the tar.gz file but you can download it from the ELMER web site... quite interesting indeed...


**There are two modes to use ELMER**

(1) using a GUI based application i.e. ELMER FRONT which has basically all the options pre-prossesing, solver and post-prossesing, however it is known that sometimes ELMERFront work and other doesn't (see FAQ at ELMER web site for more info)

(2) in case that ELMERFRoNT does not work in your PC (like in mine), you can use the second approach using ELMER Grid to set up the Mesh, then doing a bit of programming to set up the boundary and initial conditions and then using ElmerSolver to get an approximate solution to your problem. This can be seen as  Elmergrid>Solver>ElmerPost so ElmerFront is basically not required, so don't worry.

To execute ElmerFront (GUI) Type

```
ElmerFront
```

To execute ElmerGrid (Mesh generator) Type

```
ElmerGrid
```

To execute ElmerSolver (PDE solver) Type

```
Solver
```

To execute ElmerPost (Post-processing engine) type

```
ElmerPost
```

(see screenshots below)




Well have fun, for me was a highly educational LINUX experience. I really hope this helps, and hope you find this tool useful and if you find an easier way to install ELMER, also just let me know...

Finally just to acknowledge the effort of the ELMER team and thanks to them to make it available under the GLP!!!...

Cheers

---

### Post by derjames on 2006-04-23
and the screenshots....
have fun
cheers

---

### Post by Monkey_See on 2006-04-23
derjames

Thank you, very cool I have never had much luck finding a good FEA "package" in Linux.  I will have to give this a try.

---

### Post by parktownprawn on 2006-04-23
great howto - if/when you get the time why don't you post it on the wiki (wiki.ubuntu.com)?

---

### Post by adamkane on 2006-04-23
This is great!

---

### Post by Monkey_See on 2006-04-30
I'm giving the first tutorial a try, and everything runs smoothly until I try to generate the mesh.

I ran into this error:

```
/home/me/ELMER4.0/bin/ElmerMesh2D: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
```

So I looked around in synaptic to see if there were any libstdc or libc6 packages that needed to be installed, none really stood out at me.

So I did a search of my file system for "Libstdc++"... and found a link "libstdc++-libc6.2-2.so.3" going to "libstdc++-3-libc6.2-2-2.10.0.so".

So I did a:

```
sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.1-1.so.2
```

But this gave me this error when I try to generate a mesh:

```
/home/me/ELMER4.0/bin/ElmerMesh2D: Symbol `__vt_3ios' has different size in shared object, consider re-linking
/home/me/ELMER4.0/bin/ElmerMesh2D: symbol lookup error: /home/me/ELMER4.0/bin/ElmerMesh2D: undefined symbol: _t24__default_alloc_template2b1i0.free_list
```

So does anyone have any ideas about this?  Is there something that I am missing?

Thanks,

M_See

---

### Post by derjames on 2006-05-01
Hi there
For any reason that I don't know I did not have that error when installing/using ELMER, however I had the same library share problem when installing/running a different application (Funkyou, a DJ sound mixer), what I did was to install

libstdc++2.10-glibc2.2

which seems to be the same as libstdc++2.10-glibc2.2 (I am not sure about this. though) but the problem was solved

libstdc++2.10-glibc2.2 can be dowloaded via Synaptic... Anyway I will try to look for a more accurate solution for your specific problem...

cheers

---

### Post by Monkey_See on 2006-05-01
Hello,

Thanks for the response.

I checked in synaptic and I do have libstdc++2.10-glibc2.2 installed.  I tried re-installing it, but no change.

Would you have any of the libstdc development or debugging packages installed on your machine?  Just a thought.

Thanks,

M_See

---

### Post by derjames on 2006-05-05
Hi there
I have installed:

libstdc++5
libstdc++6
libstdc++6-4.0-dev
libstdc++2.10-glibc2.2

Actually I do not know what the problem might be... I did repeat tutorials 1, 2 and 3 and no problems whatsoever... Anyway I'll keep looking on that and keep you informed... 

Although ELMER seems to be a very powerful package and it is installed on my computer I am still not using it, I do need an implementation of the Volume of Fluid Method to track interfaces and ELMER is unable to compute this unless you do a bit of programming and create a new solver... However OpenFOAM has a VOF implementation ready to be used, so it is the CFD code that now I am using....

---

### Post by GAMF on 2008-11-05
> **derjames said:**
> and the screenshots....
have fun
cheers
Hi

I was wondering if any of you tried to install ElmerGui, I did but I wasn't able to compile ElmerGui.pro on hardy. If any of you have any idea please share it.

keen regrds

---

