---
title: "testing bash terminal mode/type in scripts"
date: 2009-04-23
forum: General Help
---

### Post by dim-fish on 2009-04-23
I'm trying to figure out how to test, in bash, what (mode/type/environment/?) the terminal is.  Specifically, am I opening a terminal on my desktop with a full window system or am I ssh'ing into the same machine?

I think my problem here is I don't know what to call the difference between those two, so I can't find the answer I'm looking for.

---

### Post by LateNiteTV on 2009-04-23
read the man page for the terminal youre using.

---

### Post by sdennie on 2009-04-23
If your script is just trying to determine if you are sitting physically at the machine and running a local terminal or if you are ssh'd in, you could instead check to see if the ssh daemon owns your bash shell.  I don't have a way to test this but, here is some psuedo-code (that might actually work anyway):

```

if grep $$ `pstree -p` | grep ssh ; then
# You either are or aren't local.  I can't remember the return value for grep.  ;)

```

Edit:
Hmmm.  That might not work for a script because $$ will appear on a different line in the pstree.  But, that's the basic idea from the command line.

---

### Post by Arndt on 2009-04-23
> **sdennie said:**
> If your script is just trying to determine if you are sitting physically at the machine and running a local terminal or if you are ssh'd in, you could instead check to see if the ssh daemon owns your bash shell.  I don't have a way to test this but, here is some psuedo-code (that might actually work anyway):

```

if grep $$ `pstree -p` | grep ssh ; then
# You either are or aren't local.  I can't remember the return value for grep.  ;)

```

Edit:
Hmmm.  That might not work for a script because $$ will appear on a different line in the pstree.  But, that's the basic idea from the command line.

If you're logged in with ssh, a number of environment variables will be set, with names starting with SSH_:

```
$ env|grep SSH
SSH_CLIENT=127.0.0.1 36734 22
SSH_TTY=/dev/pts/4
SSH_CONNECTION=127.0.0.1 36734 127.0.0.1 22
```

And the environment variable DISPLAY will typically not be set, but it can be set afterwards by the user.

On the other hand, is it perhaps precisely the existence of an X server that your script should test for?

---

### Post by sdennie on 2009-04-23
Listen to Arndt.  There are various ways to test and his are simpler than mine.

---

