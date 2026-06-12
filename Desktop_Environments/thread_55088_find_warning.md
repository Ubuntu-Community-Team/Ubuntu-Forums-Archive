---
title: "find: warning:"
date: 2005-08-07
forum: Desktop Environments
---

### Post by SpEcIeS on 2005-08-07
On boot I seem to be getting these errors:
```
find: warning: you have specified the -depth option after a non-option argument !, but options are not positional (-depth affects tests specified before it as well as those specified after it). Please specify options before other arguments.
``` 
```
find: warning: you have specified the -maxdepth option after a non-option argument -perm, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.
``` 
I do not know what these errors indicate. Does anybody know?  :?

---

### Post by cwaldbieser on 2005-08-07
Well, those warnings are bascally saying some script is running the "find" command, but the arguments passed to it on the command line do not appear to be in the correct order.

Could you provide a context for when this error occurs?  What are the diagnostic messages that immediately proceed and follow it?

---

### Post by SpEcIeS on 2005-08-08
[QUOTE=cwaldbieser]Well, those warnings are bascally saying some script is running the "find" command, but the arguments passed to it on the command line do not appear to be in the correct order.

Could you provide a context for when this error occurs?  What are the diagnostic messages that immediately proceed and follow it?[/QUOTE]
Yeah... I kind of got that, but these messages appear _upon booting up_. The messages were attained via boot.log.

The find application seems to work well, so I am not sure where to begin with correcting the messages.

---

### Post by cwaldbieser on 2005-08-08
[QUOTE=SpEcIeS]Yeah... I kind of got that, but these messages appear _upon booting up_. The messages were attained via boot.log.
[/QUOTE]

Right.  What I mean is, in the boot log, or during the startup sequence where all the text messages scroll up the console, were there any messages (diagnostic, error, or other) that might give a clue as to where the command was issued?  The [find] command itself is not at issue here.  Some script in the boot up sequence is doing something like:

```
#! /bin/bash

find argument --illegal-option 
```

It would be like I typed "ls -z" at the console.  There is no "z" option, but the ls command is not broken because I made a typo.

---

### Post by SpEcIeS on 2005-08-08
Absolutely, but I do not know what script. The error seems to be happening after my second hdd is mounted: /dev/hdb1.

Other than that, I thought it may be an easier issue to solve, however it seems to me that the scripts need to be grepped. :)

---

