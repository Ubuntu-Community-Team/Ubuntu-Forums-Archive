---
title: "No path - echo $path is empty"
date: 2006-05-10
forum: Desktop Environments
---

### Post by udlooz on 2006-05-10
I noticed the problem when the system couldn't find make or gcc - when I type echo $path I seem to have no path - see below:
-----------------------------------------------------------
jburk@linux:~$ echo $path

jburk@linux:~$ su
Password:
root@linux:/home/jburk# echo $path

root@linux:/home/jburk#
-----------------------------------------------------------
My profile file contains the following:
---------------------------------------------------------------------------------------------------------------
if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
fi
----------------------------------------------------------------------------------------------------------------
Help! ](*,)

---

### Post by souki on 2006-05-10
it is $PATH uppercase
anyway, your path is ok

do you have 'make' and 'gcc' installed ?
search them throught synaptic package manager

or, in a console :
```
 sudo apt-get install make gcc
```

---

### Post by ComplexNumber on 2006-05-10
> **udlooz]I noticed the problem when the system couldn't find make or gcc - when I type echo $path I seem to have no path - see below:
-----------------------------------------------------------
jburk@linux:~$ echo $path

jburk@linux:~$ su
Password:
root@linux:/home/jburk# echo $path

root@linux:/home/jburk#
-----------------------------------------------------------
My profile file contains the following:
---------------------------------------------------------------------------------------------------------------
if [ "`id -u`" -eq 0 ] said:**
> (*,) souki is right. its got to be UPPERCASE. you can find out all the enviromental variables by typing 'env'(also case sensitive, but must be lowercase) on the command line. environmental variables such as 'PATH' are uppercase.

---

### Post by udlooz on 2006-05-11
gcc-4.0-base is installed, but no other gcc package, which ones do I need to install to have a suitable C compiler so i can run ./configure?

also, make wasn't installed and the path showed up fine when I typed uppercase, I feel like a newbie for sure now.

---

