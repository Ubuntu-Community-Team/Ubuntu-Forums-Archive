---
title: "Can't run CShell scripts"
date: 2005-04-26
forum: Desktop Environments
---

### Post by sagara on 2005-04-26
I have the following issue:

I installed ubuntu at home in order to do my school work locally on my pc instead of having to telnet to the unix pc at the university.

Im writing C shell scripts for my project.  I have installed cshell in my machine but i havent been able to run my scripts.

Here is my scenario, i switch over to c shell and create the simple script **script.alpha.csh**:
```

#! /bin/csh
# prototype script

echo prototype script v1.0.1
```

I give it executable access rights, here is what **ls** displays

```
% ls -l
total 16
-rw-r--r--  1 sagara sagara   69 2005-04-25 23:59 script.1.0.1~
-rwxr-xr-x  1 sagara sagara   72 2005-04-25 23:59 script.alpha.csh
-rwxr-----  1 sagara sagara 2051 2005-03-09 16:08 script.csh
-rwxr-----  1 sagara sagara 2051 2005-03-06 20:54 smurfQ.csh
```

But when I try to run it I get the following error:
```
% script.alpha.csh
script.alpha.csh: Command not found.
```

What am I missing in order to be able to run my cshell scripts?

---

### Post by GrumpySmurf on 2005-04-26
You don't have the current directory (.) in your path.

If your shell is csh, 

```
% setenv PATH $PATH:.
```
Add that to your .tcshrc, .cshrc or whatever csh calls when it initializes.  Alternately, specify the full path to your script

```
% /home/user/script.alpha.csh
```
Disclaimer: I don't use csh.

---

### Post by sagara on 2005-04-26
thanks GrumpySmurf, your feedback sure helped!  :razz: 

after looking around I found out that the correct way to modify the **path environmental variable** was:

```
setenv PATH $PATH":."
```

I created my .cshrc file in my local directory then added that line and now I can run my scripts.  Thanks again!

---

### Post by GrumpySmurf on 2005-04-26
[QUOTE=sagara]thanks GrumpySmurf, your feedback sure helped!  :razz: 

after looking around I found out that the correct way to modify the **path environmental variable** was:

```
setenv PATH $PATH":."
```

I created my .cshrc file in my local directory then added that line and now I can run my scripts.  Thanks again![/QUOTE]
 At least I was close ;).

You're welcome, glad I could help.

---

