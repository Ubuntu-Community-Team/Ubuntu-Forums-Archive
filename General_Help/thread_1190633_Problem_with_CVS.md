---
title: "Problem with CVS"
date: 2009-06-18
forum: General Help
---

### Post by codingfreak on 2009-06-18
Hi

I am a newbie to Linux. I am trying to setup a working CVS in a FEDORA 9 machine. So googled through and came across some documents on "**How to setup CVS and use it**".

I decided to create my CVSROOT at /home/cvsroot
```

$mkdir /home/cvsroot

$chgrp cvsusers /home/cvsroot

Even set the Stickybit by using the following command
$chmod g+srwx /home/cvsroot

Initialized CVS
$cvs -d /home/cvsroot init

Changed the ownership to a user named 'cvs'
$chown -R cvs /home/cvsroot

$ls -al /home/cvsroot
total 12
drwxrwsr-x  3 cvs  cvsusers 4096 2009-06-17 15:03 .
drwxr-xr-x 24 root root     4096 2009-06-17 15:45 ..
drwxrwsr-x  3 cvs  cvsusers 4096 2009-06-17 15:03 CVSROOT
```Now I logged into a user named 'freak' who is under the usergroup 'cvsusers' and tried to import the project

$cvs -d /home/cvsroot import sesame test ver_0-1

But I got the following error
```
cvs import: cannot make path to /home/cvsroot/sesame: Permission denied
cvs import: failed to create lock directory for `/home/cvsroot/sesame' (/home/cvsroot/sesame/#cvs.lock): No such file or directory
cvs import: lock failed - giving up
N sesame/Day.txt
cvs import: ERROR: cannot write file /home/cvsroot/sesame/Day.txt,v: No such file or directory
N sesame/Number.txt
cvs import: ERROR: cannot write file /home/cvsroot/sesame/Number.txt,v: No such file or directory
cvs import: Importing /home/cvsroot/sesame/.svn
cvs import: ERROR: cannot mkdir /home/cvsroot/sesame/.svn -- not added: No such file or directory

No conflicts created by this import
```So I followed the document at [http://rimuhosting.com/howto/cvs.jsp](http://rimuhosting.com/howto/cvs.jsp). It says
```
If you get an error like:

cvs import: cannot make path to /usr/local/cvsroot/someproj: Permission denied
cvs import: Importing /usr/local/cvsroot/someproj/someproj
cvs import: ERROR: cannot mkdir /usr/local/cvsroot/someproj/someproj -- not added: No such file or directory

Then check that the user is in the cvs user's group, and that the sticky bit was set for the cvs group on the /usr/local/cvsroot directory.

The /usr/local/cvsroot/CVSROOT directory created by cvs init includes the cvswrappers file.  You should probabably add a list of your binary file types there (see below).
```When I checked if my stick bit is set or not I found that 

```
drwxrwsr-x  3 cvs      cvsusers 4096 2009-06-17 15:03 cvsroot
```I came to know that there should be a T if the sticky bit is set but there is none here.

So can anyone help me out .... Even if i try to set it I am not getting the 't' symbole and still I am getting the permission denied problem.

---

