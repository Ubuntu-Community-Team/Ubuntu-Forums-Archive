---
title: "downgrade gcc-version to compile mex-files for matlab???"
date: 2010-02-22
forum: Desktop Environments
---

### Post by margarita333 on 2010-02-22
I am trying to run matlab 7.7 (R2008b) on my ubuntu 9.10 distribution..the thing is that I am totally new with both matlab and linux and I get the following error message from matlab when I try to run an example mex-function:

>> mex yprime.c

/home/margareta/Desktop/matlab/bin/mex: 1572: gcc: Permission denied

Warning: You are using gcc version "".  The earliest gcc version supported
         with mex is "4.0.0".  The latest version tested for use with mex is "4.2.0".
         To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org) 

eval: 1: gcc: Permission denied

    mex: compile of ' "yprime.c"' failed.

??? Error using ==> mex at 213
Unable to complete successfully.

I had gcc-4.4 as default on my pc, so after this error I downloaded an older version (gcc-4.1) and removed with rm the symbolic link in /usr/bin pointing to gcc-4.4 and created a new one pointing to gcc-4.1. Now when I type gcc -v in the terminal it says that gcc is in the packages gcc and pentium-builder, suggesting to do an apt-get install. I tried that but than it says that gcc-4.1 is already the newest version.
Can anyone help me please? It seems that I have multiple versions of gcc installed but neither the terminal nor matlab can find them. What did I wrong? and HOW can I solve it???

---

### Post by 3Miro on 2010-02-22
The gcc version issue is only a warning. The real problem is the permissions on mex.

What are the permissions on:

/home/margareta/Desktop/matlab/bin/mex

Try
```

l -l /home/margareta/Desktop/matlab/bin/

```
from the terminal. Also, yprime.c, wherever that file might be.

---

### Post by margarita333 on 2010-02-22
[B]Hey,
thanks for helping me..
I tried what you suggested, guessing that you mean ls -l, because l -l doesn't seem to work:
[/B]
:~$ ls -l /home/margareta/Desktop/matlab/bin/
total 544
-rwxr-xr-x 1 margareta margareta  18593 2008-08-05 00:27 activate_matlab.sh
-rwxr-xr-x 1 margareta margareta  17718 2008-08-05 00:27 deactivate_matlab.sh
-rwxr-xr-x 1 margareta margareta  10228 2008-08-05 00:06 engopts.sh
-rwxr-xr-x 1 margareta margareta  13256 2008-08-05 00:06 f90opts.sh
-rwxr-xr-x 1 margareta margareta  12443 2008-08-05 00:06 gccopts.sh
drwxr-xr-x 5 margareta margareta  20480 2010-02-07 00:36 glnx86
-rw-r--r-- 1 margareta margareta     19 2008-05-24 01:18 insttype.ini
-rw-r--r-- 1 margareta margareta 109093 2008-05-24 01:18 lcdata.xml
-rwxr-xr-x 1 margareta margareta   1541 2008-05-24 01:18 lcdata.xsd
-rwxr-xr-x 1 margareta margareta  10835 2008-08-05 00:06 ldd
-rwxr-xr-x 1 margareta margareta  53559 2008-08-05 00:06 matlab
-rwxr-xr-x 1 margareta margareta  10227 2008-08-05 00:06 matopts.sh
-rwxr-xr-x 1 margareta margareta  75098 2008-08-05 00:06 mbuild
-rwxr-xr-x 1 margareta margareta  11038 2008-08-05 00:06 mbuildopts.sh
-rwxr-xr-x 1 margareta margareta  43130 2008-08-05 00:06 mcc
-rwxr-xr-x 1 margareta margareta  50530 2008-08-05 00:06 mex
-rwxr-xr-x 1 margareta margareta   8778 2008-08-05 00:06 mexext
-rwxr-xr-x 1 margareta margareta  13260 2008-08-05 00:06 mexopts.sh
-rwxr-xr-x 1 margareta margareta    758 2008-05-24 01:18 mw_mpiexec
-rwxr-xr-x 1 margareta margareta    567 2008-05-24 01:18 mw_smpd
-rwxr-xr-x 1 margareta margareta   7286 2008-08-05 00:06 optsetup.sh
drwxr-xr-x 2 margareta margareta   4096 2010-02-07 00:34 registry
drwxr-xr-x 2 margareta margareta   4096 2010-02-07 00:24 scripts
drwxr-xr-x 3 margareta margareta   4096 2010-02-07 00:24 util
-rwxr-xr-x 1 margareta margareta    531 2008-05-24 01:18 worker

[B]what do you think should I do? the yprime.c file is just an example file from matlab, to see if the mex-function works. I am actually trying to call a function from mrVista where the readNiftiFile.mexglx me gives this error message:
[/B]
??? Invalid MEX-file
'/home/margareta/Desktop/matlab/svn/vistasoft/trunk/fileFilters/nifti/readFileNifti.mexglx':
/usr/local/matlab/r2007a/bin/glnx86/libz.so: cannot open shared object file: No such
file or directory
[B]
Any idea???[/B]

---

### Post by 3Miro on 2010-02-22
I have aliased l and ls and I only use the short one. Sorry for the confusion.

Check the permissions on the file yprime.c and the folder where that file is. Use:
```
ls -al
```
The folder should have write permissions and the file should have read permissions.

I tried using Mex from Matlab 8 on Ubuntu 9.10. Installing 
```
sudo apt-get install gcc-4.1-multilib 
```
from the repos and changing the symlink in /usr/bin/gcc got rid of the warning for me. The problem is with permissions not gcc version, but just in case, here is how you can change the symlink:
```

sudo mv /usr/bin/gcc /usr/bin/gcc_mybackup
sudo ln -s /usr/bin/gcc-4.1 /usr/bin/gcc

```

If you want to compile something else and want to use gcc-4.4, you can either call gcc-4.4 directly or restore the symlink
```
sudo mv /usr/bin/gcc_mybackup /usr/bin/gcc
```

---

### Post by margarita333 on 2010-02-23
hey miro

I did what you suggested...so happy that you are helping me..now here is the next matlab error message: it seems that now it's not the permission anymore but matlab just can't find the gcc:

/home/margareta/Desktop/matlab/bin/mex: 1572: gcc: not found

Warning: You are using gcc version "".  The earliest gcc version supported
         with mex is "4.0.0".  The latest version tested for use with mex is "4.2.0".
         To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org) 

eval: 1: gcc: not found

    mex: compile of ' "yprime.c"' failed.

??? Error using ==> mex at 213
Unable to complete successfully.

Should I maybe make a symbolic link in the mex folder, or better in the /home/margareta/Desktop/matlab/bin folder pointing to the gcc-4.1???
Now the symbolic link in /usr/bin/ seems to be fine:

:~$ ls -l /usr/bin/gcc
lrwxrwxrwx 1 root root 16 2010-02-23 09:55 /usr/bin/gcc -> /usr/bin/gcc-4.1

But the version is still not detected by the terminal:

~$ gcc -v
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
gcc: command not found

What do you think is the problem?

---

### Post by 3Miro on 2010-02-23
This is very strange. For some reason it cannot find gcc despite it being in /usr/bin. Lets try to find the problem:

Try
```
which gcc
```
this should tell you if it can find a specific command and where it can be found. It should return /usr/bin/gcc.

Try
```

ls -l /usr/bin/gcc*

```
should return all the files in /usr/bin/ that start with gcc. You should have something that looks like:
```

lrwxrwxrwx 1 root root     16 2010-02-22 18:06 /usr/bin/gcc -> /usr/bin/gcc-4.1
-rwxr-xr-x 1 root root 226736 2009-08-27 07:49 /usr/bin/gcc-4.1
-rwxr-xr-x 1 root root 251096 2010-01-10 11:54 /usr/bin/gcc-4.4
-rwxr-xr-x 1 root root  16296 2009-08-27 07:47 /usr/bin/gccbug-4.1
-rwxr-xr-x 1 root root 251096 2010-02-22 18:05 /usr/bin/gcc_mbackup

```
You can look for the permissions of the /usr/bin/ folder itself:
```
ls -l /usr/ 
```
and look for 
```
drwxr-xr-x   2 root root  73728 2010-02-22 18:06 bin
```

The way Ubuntu knows where to look for commands is in the $PATH variable. It is basically a list of folders where executable files can be found. Try
```
 $PATH 
```
you should get something like
```
bash: /home/mnz/bin:/home/mnz/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
```
Look for :/usr/bin/:, if it is not there, you can open .bashrc
```
gedit .bashrc
```
and at the very bottom of the file add
```
PATH="/usr/bin:$PATH"
```
and then restart the terminal (close the window and open it again). Change .bashrc only if /usr/bin is not in $PATH.

---

### Post by Ruesca on 2010-11-04
I had similar problems with mex-files and eventually I had to downgrade my gcc compiler as well.

What I did to use mex-files on my Ubuntu 10.04 with MATLAB 7.11.0 (R2010b) was:

[LIST=1]
[*]downgrade the gcc compiler to version 4.3 
```
 sudo apt-get install gcc-4.3
```
[*]downgrade the g++ compiler also to version 4.3
```
 sudo apt-get install g++-4.3
```
[*]change the symbolic links in /usr/bin as described above
```
sudo ln -s gcc-4.3 gcc
sudo ln -s g++-4.3 g++

```
[*]install the old libstdc++ version (in my case) 
```
 sudo apt-get install libstdc++6-4.3-dev 
```
[*]finally in MATLAB setup the mex-compiler with 

```
 mex -setup 
```
[/LIST]
and you're done!

I don't know if this solves your problem, but that's the way I set it up. Specially the 4th point is really important, and actually was the reason why it didn't work in my case first.

- cheers

---

