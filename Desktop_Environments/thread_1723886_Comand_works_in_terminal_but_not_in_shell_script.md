---
title: "Comand works in terminal but not in shell script"
date: 2011-04-07
forum: Desktop Environments
---

### Post by 71GA on 2011-04-07
Hello!

If i type command 
```
export ROOT=$(pwd)
```
directly into a terminal i can see my current directory as a value of enviromental variable ROOT. I can check it with printenv command. 

Same command does nothing when executed from a script. Why???




Regards Ziga

---

### Post by DaithiF on 2011-04-08
Hi, actually it does exactly the same thing when run in a script.

e.g.: create a script with these contents and run it ... you should see that ROOT gets set.
```
#!/bin/bash
export ROOT=$(pwd)
echo "in script, ROOT is $ROOT"
echo "and we can see it in printenv's output too: $(printenv | grep ROOT)"

```

I'm guessing that you are also expecting the value of $ROOT to be set after the script has finished executing though.  Thats won't be the case ... variables are set in a particular shell environment.  when a script executes it runs in its own (new) shell environment.  It is a subshell of the parent process (your interactive terminal session).  And while the script can do whatever it wants within its own shell environment, and can also populate variables for subsequent subshells of itself (via the export command), it can't affect the environment of its parent.

So ROOT is only set in the subshell environment of the running script, and your terminal session doesn't know anything about it.

You can maybe achieve what you want by doing:
```
source yourscript
```
or
```
. yourscript

```
these do the same thing, which is to execute the commands within the script one at a time within the current shell environment rather than execute the script in a new subshell.

---

