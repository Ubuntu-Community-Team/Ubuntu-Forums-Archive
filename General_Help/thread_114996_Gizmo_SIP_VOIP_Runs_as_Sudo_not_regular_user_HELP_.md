---
title: "Gizmo SIP VOIP: Runs as Sudo not regular user HELP THE NOOB"
date: 2006-01-09
forum: General Help
---

### Post by bennettg on 2006-01-09
Please help this noob.

I wanted to use the gizmoproject sip/voip (like skype).  I followed the directions on their page for debian install:

To install Gizmo Project on Debian, the following Debian packages must be installed in order:

   1. Bonjour - A networking library from Apple. More information can be found here.
   2. libsipphoneapi - This is the main library for Gizmo Project, it is common to all of our versions.
   3. gizmo-project - This file is specific to the Linux version, and contains the User Interface

I used the sudo ppkd -i XXXXXXX.deb command

After installing the 3 files, I try to run gizmoproject as a regular user and I get this error:

KDEInit could not launch 'audiowrapper'.:
Could not find 'audiowrapper' executable.


But when I run gizmo as root, the program launches just fine.


what am i doing wrong.  please help this nooob.  i tried to search the forum, but didnt find an answer.  the forums on the gizmoproject site did not help either,

---

### Post by schilcha on 2006-01-10
First of all a disclaimer: I've never heard of gizmo, but I'll try to help anyways...

First of all, two straight-forward guesses:
**You (as user) cannot find "audiowrapper"**
Enter the following commands in a terminal:
```

sudo which audiowrapper
which audiowrapper

```
If you get some output from the first, but not from the second command, here's the solution: add the path to audiowrapper (removing the trailing "audiowrapper" from the output) to your PATH-environment. Add the line 
```

export PATH="$PATH:/path/to/audiowrapper/directory"

```
to the file ".bashrc" in your home-dir (e.g. "gedit ~/.bashrc")

**You (as user) are not allowed to run "audiowrapper"**
Again, on a terminal enter the command
```

sudo ls -l `which audiowrapper`

```
Does it look like "-rwxr-xr-x   1 root   root ..." -- that's fine
or does it look like this "-rwxr--r--   1 root   root" (the x's matter!) -- that's bad. In this case execute
```

sudo chmod a+x `which audiowrapper`

```

Good Luck!

---

### Post by bennettg on 2006-01-10
[QUOTE=schilcha]First of all a disclaimer: I've never heard of gizmo, but I'll try to help anyways...

First of all, two straight-forward guesses:
**You (as user) cannot find "audiowrapper"**
Enter the following commands in a terminal:
```

sudo which audiowrapper
which audiowrapper

```
If you get some output from the first, but not from the second command, here's the solution: add the path to audiowrapper (removing the trailing "audiowrapper" from the output) to your PATH-environment. Add the line 
```

export PATH="$PATH:/path/to/audiowrapper/directory"

```
to the file ".bashrc" in your home-dir (e.g. "gedit ~/.bashrc")

**You (as user) are not allowed to run "audiowrapper"**
Again, on a terminal enter the command
```

sudo ls -l `which audiowrapper`

```
Does it look like "-rwxr-xr-x   1 root   root ..." -- that's fine
or does it look like this "-rwxr--r--   1 root   root" (the x's matter!) -- that's bad. In this case execute
```

sudo chmod a+x `which audiowrapper`

```

Good Luck![/QUOTE]

No Luck.  I am a dumb nOOb.  here is the output:


bennettg@ubuntu:~$ which audiowrapper
bennettg@ubuntu:~$ sudo ls -l `which audiowrapper`
total 9584
-rw-r--r--  1 bennettg bennettg   29754 2006-01-08 18:19 automatix-kubuntu_1.5-2_i386.de
b
-rw-r--r--  1 bennettg bennettg     297 2006-01-08 19:58 automatix-kubuntu.log
-rw-r--r--  1 bennettg bennettg  126220 2006-01-09 17:53 bonjour_107.1-0.0.0.50.linspire
0.2_i386.deb
drwx------  2 bennettg bennettg    4096 2006-01-09 17:32 Desktop
-rw-r--r--  1 bennettg bennettg 6722834 2006-01-09 17:53 gizmo-project_1.0.0.17-1_i386.d    eb
-rw-r--r--  1 bennettg bennettg   26430 2005-10-12 17:59 kubuntu-packages-jriddell-key.g    pg
-rw-r--r--  1 bennettg bennettg 2864108 2006-01-09 17:53 libsipphoneapi_0.78.20051209-1_    i386.deb
drwxr-xr-x  3 bennettg bennettg    4096 2006-01-09 17:54 My_Documents
bennettg@ubuntu:~$



Please help again.  Thanks

PS gizmo is like skype, but cheaper.  [www.gizmoproject.com](www.gizmoproject.com)  run by michael robertson from mps.com/linspire

---

### Post by schilcha on 2006-01-11
I tried to have a look at the problem... other people had similar errors... Your error doesn't seem to be as straight forward as I thought.

Have a look at [post #94]("http://www.ubuntuforums.org/showthread.php?p=569162") and the following. Obviously this is related to applications not being able to share the sound-hardware correctly. 

I'm sorry I can't help you more right now -- I don't really want to do the installation you did and probably mess up my installation.

---

