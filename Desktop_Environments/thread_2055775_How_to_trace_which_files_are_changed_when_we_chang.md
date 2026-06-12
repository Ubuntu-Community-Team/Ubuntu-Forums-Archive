---
title: "How to trace which files are changed when we change an application's configuration"
date: 2012-09-10
forum: Desktop Environments
---

### Post by devaj on 2012-09-10
Hi, I would like to know is there any application or command to trace the files that are changed whenever we change a configuration parameter of an application via it's graphical interface. 
 Say when changing the Calculator's show decimal places parameter through it's preference menu,I would love to have an application or a command that looks over which files (only the name of the files any other feature would be a plus) are being affected via this action .I Hope I have made myself clear.Do let me know if you need any more clarification.

---

### Post by Frogs Hair on 2012-09-10
Each application has a configuration file/s and by entering properties with a right click the accessed and modified date are displayed. A specific change may be difficult to find though.

---

### Post by TheFu on 2012-09-10
> **devaj said:**
> Hi, I would like to know is there any application or command to trace the files that are changed whenever we change a configuration parameter of an application via it's graphical interface. 
 Say when changing the Calculator's show decimal places parameter through it's preference menu,I would love to have an application or a command that looks over which files (only the name of the files any other feature would be a plus) are being affected via this action .I Hope I have made myself clear.Do let me know if you need any more clarification.

The program you seek is called **find**.  Check out the **mtime **option.
```
$ man find
```will explain everything, but something like the following should work:
```
$ find /some/directory -mtime -1 
```to find all files modified in the last hour.  If that isn't fine enough detail, you can pipe that output through **grep** to look for specific hh:mm timestamps. You'll want to add the** -ls** option so that data is available for the grep.

If you want the output sorted in some way, you can pipe THAT output through **sort** and pick the columns, places to be sorted forward or reverse .... 

This is the core power of UNIX-like OSes.  Once you solve this problem, save it as a script for later use. You'll never really have to solve it again.  I have hundreds ... er .... thousands of little scripts like this.  Many are run every day, automatically, to do things** for me** - like computers are supposed to.  The results are emailed to me, so I don't need to hunt them down.

---

