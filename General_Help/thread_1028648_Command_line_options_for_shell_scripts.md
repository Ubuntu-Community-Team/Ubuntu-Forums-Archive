---
title: "Command line options for shell scripts"
date: 2009-01-02
forum: General Help
---

### Post by ulvesang on 2009-01-02
I've searched for this idiodically-simple answer but I can't actually seem to find it.

What variable can I use inside a shell script to make my script modifiable by the command line? I.e.

$script [VARIABLE?]

script.sh:
-----------
killall [VARIABLE?]
[VARIABLE?]
-----------

---

### Post by lykwydchykyn on 2009-01-02
You can refer to the command line arguments using the variables $1, $2, $3, etc.

In other words, the first argument after the script name is $1, the second $2, and so forth.  The name of the script is $0, which is useful in some situations.

---

### Post by BuudWeizErr on 2009-01-02
isn't it $1?

e; fb.

---

### Post by kaibob on 2009-01-02
Some other variables that may be of help:

$0   The name of the current script.
$1   The first argument passed to the shell
$#   The number of arguments passed to the shell
$*   The values of all the positional parameters as a single value
$@   The same as $* except when double quoted it has the effect of double-quoting each parameter
$$   The PID of the current shell
$!   The PID of the last program sent to the background
$?   The exit status of the last command
$-   lists the current options

---

