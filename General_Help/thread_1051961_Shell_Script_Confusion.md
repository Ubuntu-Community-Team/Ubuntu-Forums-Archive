---
title: "Shell Script Confusion"
date: 2009-01-27
forum: General Help
---

### Post by echo8413 on 2009-01-27
We are currently studying Ubuntu in my college class, and my professor introduced shell scripts to us today. Here is the script we are using:

#
# This scrip will be used to print user information for the current user, current date & time, and a calendar.
#
clear
echo "Hello $USER"
echo "Today is";date
echo "Number of User Login:";who|wc -l
echo "Calendar"
cal
exit 0


There are breaks where the semi-colons are is there any way to prevent the break in the script.

---

### Post by mcduck on 2009-01-27
Do you mean line breaks? Easy fix:

```
#/bin/sh
clear
echo "Hello $USER"
echo  -n "Today is";date
echo  -n "Number of User Login:";who|wc -l
echo "Calendar"
cal
exit 0
```

You could also do this:
```
#/bin/sh
clear
echo "Hello $USER"
echo "Today is" `date`
echo "Number of User Login:" `who|wc -l`
echo "Calendar"
cal
exit 0
```
The difference is that your code runs first echo, then those commands. (using semi-colon is the same as if you'd put the command on next line). What my example does is that it runs the commands *inside* the echo command, not after it. (putting the command inside backticks instead of separating it with a semicolon does this.)

..or store the results from those commands as variables and use them in the echo commands:
```
#/bin/sh
clear
thisDate=`date`
loginNumber=`who|wc -l`
echo "Hello $USER"
echo "Today is " $thisDate 
echo "Number of User Login:" $loginNumber
echo "Calendar"
cal
exit 0
```

---

### Post by echo8413 on 2009-01-27
Doing that the who command and the date command no longer work properly.

---

### Post by mcduck on 2009-01-27
> **echo8413 said:**
> Doing that the who command and the date command no longer work properly.

Then you are using wrong character, it's supposed to be backtick, not a single quote or normal tick.

---

### Post by echo8413 on 2009-01-27
Yeah I think that is what it is. Thanks for your help cuz I did put in the wrong character.

---

