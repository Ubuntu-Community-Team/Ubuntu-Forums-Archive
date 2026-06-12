---
title: "Issue with variable expansion in bash scripts"
date: 2009-05-01
forum: General Help
---

### Post by avam323 on 2009-05-01
I am writing a script that uses the system variable $HOSTNAME as part of a mkdir command:
```
mkdir /STORAGE/BACKUP/.tmp/$HOSTNAME
```
Now while this works as expected just entering the code at the terminal, for some reason, the $HOSTNAME variable comes up null when the script is launched (says /STORAGE/BACKUP/.tmp/ exists). The problem here seems to be the fact that $HOSTNAME has not been initialized in the script (but I can use it on the command line); my question is how to read from the system-wide environment variables from inside a script.

To be fair, I understand the simplest workaround would be to do something like this:
```

#!/bin/sh
# set date in mm-dd-yyyy format
Today="`date +%m%d%Y`"
# set a variable to take the place of $HOSTNAME
Hname=MYPC
mkdir /STORAGE/BACKUP/.tmp/$Hname

```

But surely there is a way to access an environment variable from inside a script... Thank you in advance :)

---

### Post by Rocket2DMn on 2009-05-03
Moved to General Help - please don't post support questions in Tutorials & Tips.  Threads there are for guides and HowTos only, and require staff approval.

In Ubuntu, /bin/sh uses Dash instead of Bourne Shell (see [uwiki]DashAsBinSh[/uwiki]).  By default, Ubuntu uses the Bash shell for terminal, so you would have better luck if you use /bin/bash instead of /bin/sh.  Alternatively you can take the route you are currently using and call /bin/hostname
```
Hname=`/bin/hostname`
```
to assign the true hostname to the variable.

---

### Post by avam323 on 2009-05-05
My apologies. Thank you for the feedback and extra information as well. I've never really used forums much, and to be honest, I had no idea where to put it due to the nature of this issue. I couldn't tell what the prob was, but you are indeed right about my problem. That fixed four scripts I've been working on lately. I thank you for your time. :D

---

### Post by life-on-mars on 2009-07-27
```
HOSTNAME=$(hostname)
```

This works as well (more useful for users of keyboards with dead keys). I would also give the variable the originally intended name ($HOSTNAME) for possible future changes and ports.

Interestingly other variables like $USER seem to work with dash. Must be a POSIX thing that $USER made it into dash and $HOSTNAME did not. :biggrin:

According to `man dash` the dash shell reads /etc/profile, so you could also set the variable there.

---

